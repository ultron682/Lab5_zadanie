# Lab 5 Programowanie Full-stack w Chmurze Obliczeniowej

## Opis

Projekt implementuje zarządzanie zasobami w Kubernetes dla dwóch środowisk: dev i prod.

## Struktura namespace

- **ns-dev**: środowisko deweloperskie

  - CPU requests: 1, limits: 2
  - Memory requests: 1Gi, limits: 2Gi
  - Max 10 podów
  - Domyślne limity per container: CPU 0.2, Memory 256Mi

- **ns-prod**: środowisko produkcyjne
  - CPU requests: 2, limits: 4
  - Memory requests: 2Gi, limits: 4Gi

## Deploymenty testowe

### no-test

Deployment z zasobami przekraczającymi limity (0.3 CPU, 512Mi RAM).

### yes-test

Deployment spełniający wymagania (0.1 CPU request, 0.2 CPU limit, 128Mi/256Mi memory).

### zero-test

Deployment bez deklaracji zasobów.
Automatycznie otrzymuje domyślne wartości z LimitRange

## Weryfikacja czy śmiga

kubectl describe limitrange -n ns-dev
