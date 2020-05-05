---
title: kotlinx.serialization
caption: JSON support using kotlinx.serialization
category: servers
feature:
  artifact: io.ktor:ktor-serialization:$ktor_version
  class: io.ktor.serialization.SerializationConverter
redirect_from:
- /features/serialization.html
- /features/content-negotiation/serialization.html
ktor_version_review: 1.2.3
---

The SerializationConverter feature allows you to handle JSON content in your application easily using
[kotlinx.serialization](https://github.com/Kotlin/kotlinx.serialization) library.

This feature is a [ContentNegotiation](/servers/features/content-negotiation.html) converter.

{% include feature.html %}

## Basic usage

To install the feature by registering a JSON content convertor using kotlinx.serialization:

```kotlin
install(ContentNegotiation) {
    json()
}
```

## Configuration

The `json()` function has two optional parameters with default arguments:
* `contentType` provides a way to specify which content types it should handle, `ContentType.Application.Json` by default.
* `json` provides ability to configure [JSON formatter](https://github.com/Kotlin/kotlinx.serialization/blob/master/docs/runtime_usage.md#json), `Json(DefaultJsonConfiguration)` by default.

Advanced example:
```kotlin
install(ContentNegotiation) {
    json(
        contentType = ContentType.Application.Json,
        json = Json(
            DefaultJsonConfiguration.copy(
                prettyPrint = true
            )
        )
    )
}
```

