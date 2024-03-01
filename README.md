# pirsch.io

The website for pirsch.io.

## Structure

The directory structure is as follows:

| Directory | Description |
| - | - |
| content/ | Recursive content files in JSON format. |
| static/ | Static content (will be served as is on `/static/`). |
| style/ | Sass npm project compiling the output to `static/css/` |
| tpl/ | Recursive Golang template files. |

The JSON structure for a content file is as follows:

```json
{
    "path": {
        "en": "/",
        "de": "/de"
    },
    "content": {
        "content": [
            {
                "ref": "head" // references to a standalone element (JSON file without extension, always lowercase)
            },
            {
                "tpl": "test", // template file (without extension, always lowercase)
                "data": { // optional data used in the template
                    "en": {
                        "headline": "Welcome!",
                        "text": "To pirsch.io."
                    },
                    "de": {
                        "headline": "Willkommen!",
                        "text": "Bei pirsch.io."
                    }
                },
                "content": {
                    "children": [ /* ... */ ]
                }
            }
        ]
    }
}
```

Standalone elements are use the same structure as pages, but do not specify paths. Here is an example:

```json
{
    "tpl": "head",
    "data": {
        "en": {
            "title": "Welcome to Pirsch"
        },
        "de": {
            "title": "Willkommen bei Pirsch"
        }
    }
}
```
