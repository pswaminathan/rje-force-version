# rje-force-version

Example demonstrating `rules_jvm_external` not respecting `force_version` in a bzlmod context.

In MODULE.bazel:

```
maven.artifact(
    artifact = "okio",
    group = "com.squareup.okio",
    version = "3.7.0",
    force_version = True,
)
```

But in `maven_install.json`:

```
  "conflict_resolution": {
  	...
    "com.squareup.okio:okio:3.7.0": "com.squareup.okio:okio:2.10.0"
  },
```

These dependencies are coming from `grpc-java`.
