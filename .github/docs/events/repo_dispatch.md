Steps for triggering workflow from repo dispatch event

1. Ensure workflow has repository_dispatch event hook:

```yml
on:
  repository_dispatch:
    type: [build]
```

2. Generate token with repo access in github

3. Create API POST request:

- POST URL: https://api.github.com/repos/OWNER/REPO/dispatches
- Request body:

```json
{
    "event_type": "build"
}
```

- Use basic auth authorisation, using generated token as password

4. To pass in extra information, e.g. environment variables, use client_payload in body:

```json
{
    "event_type": "build",
    "client_payload": {
        "env": "production"
    }
}
```

Further resources:
https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#repository_dispatch
https://docs.github.com/en/rest/repos/repos?apiVersion=2022-11-28#create-a-repository-dispatch-event
