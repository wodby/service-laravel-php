# PHP (Laravel) service for Kubernetes on Wodby

Build and run PHP (Laravel) applications on Kubernetes with Wodby.

This repository defines the Wodby service manifests and operational
configuration for PHP (Laravel).

- [Browse Wodby services](https://wodby.com/services)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Start with a boilerplate

Use one of the boilerplates exposed by this service to start with compatible
build configuration and Wodby CI:

- [Laravel on Wodby](https://github.com/wodby/laravel-boilerplate)

## Wodby stacks using this service

- [Laravel application stack](https://github.com/wodby/stack-laravel)

## Service overview

| Property | Manifest configuration |
| --- | --- |
| Service name | `laravel-php` |
| Type | Application service |
| Inherits from | [`php`](https://github.com/wodby/service-php) with version constraint `^1.0.0` |
| Versions | `8.4` by default; also available: `8.5`, `8.3`, `8.2` |
| Workloads | `main` (Deployment), primary |
| Containers | `php` using `wodby/laravel-php`, build target |
| Service links | Storage, required, Redis, optional |
| Volumes | Storage, 10 GB, shared, linked through `storage` |
| Application build | Git source connection enabled; Dockerfile: `Dockerfile`; boilerplates: Laravel on Wodby |
| Configuration | 1 generated or fixed tokens |
| Operations | 2 actions, 1 cron schedules |

The Wodby Laravel boilerplate requires PHP `^8.3`. PHP 8.2 remains available when using a connected repository.

## Use this service

Use this service through [Laravel application stack](https://github.com/wodby/stack-laravel), or reference `laravel-php` from a
custom Wodby stack.

A service is a reusable component and does not deploy by itself. The stack
defines its links, settings, versions, resources, and relationship to the rest
of the application.

## Maintain a custom version

1. Fork this repository.
2. Edit the service manifest and referenced files.
3. Import the repository as a [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference the service from a stack manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time.

Validate the manifests with:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/) and the [managed services index](https://github.com/wodby/services).
