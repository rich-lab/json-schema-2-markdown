# json-schema-2-markdown

[![NPM version](https://badgen.net/npm/v/json-schema-2-markdown)](https://npmjs.com/package/json-schema-2-markdown) [![NPM downloads](https://badgen.net/npm/dm/json-schema-2-markdown)](https://npmjs.com/package/json-schema-2-markdown) [![CircleCI](https://badgen.net/circleci/github/ulivz/json-schema-2-markdown/master)](https://circleci.com/gh/ulivz/json-schema-2-markdown/tree/master)

## Install

```bash
tnpm install json-schema-2-markdown --save
```

## Example

- `Input`: 

```json
{
  "title": "foo.config.js",
  "description": "My Config File",
  "properties": {
    "type": {
      "description": "TYPE's description",
      "type": "string",
      "enum": [
        "foo",
        "bar"
      ]
    },
    "env": {
      "description": "ENV's description",
      "type": "string"
    }
  }
}
```

- `Output`:

```md
# foo.config.js
 
My Config File

## type

- Type: `"foo" | "bar"`
- Description: TYPE's description

## env

- Type: `string`
- Description: ENV's description"
```

## Usage

```js
const { transform } = require('json-schema-2-markdown')

transform({
  schemaPath: 'fixtures/simple.json',
  outputPath: 'docs/config/README.md',
})
```

## API

### .transform()

- Type: `(options: ITransformOptions) => Promise<string>`
- Description: `Get markdown output by JSON Schema.`

Type of `ITransformOptions` is as follows:

```typescript
interface ITransformOptions {
  /**
   * Current working directory, used to calcaulate absolute path for "schemaPath"
   * and "outputPath" with relative path, defaults to `process.cwd()`.
   */
  cwd?: string;
  /**
   * A relative path or an absolute path to a JSON Schema file. 
   */
  schemaPath: string;
  /**
   * A relative path or an absolute path to a output markdown file.
   */
  outputPath: string;
  /**
   * Whether to write output content to "outputPath".
   */
  write: boolean;
  /**
   * Current locale.
   */
  locale: string;
  /**
   * Specify a markdown file to be merged into the generated markdown.
   */
  schemaMarkdown: string;
  /**
   * Frontmatter content.
   */
  frontmatter: string;
  /**
   * Content at the below of h1.
   */
  heading: string;
  
}
```

### .batchTransform()

- Type: `(options: IBatchTransformOptions) => Promise<string[]>`
- Description: `Get markdown output by JSON Schema.`

Type of `IBatchTransformOptions` is as follows:

```typescript
interface IBatchTransformOptions {
  /**
   * Global "cwd".
   */
  cwd: string;
  /**
   * Global "cwd".
   */
  locale: string;
  /**
   * Global "write".
   */
  write: string;
  /**
   * Meta transform config.
   */
  configs: ITransformOptions[];
}
```

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D


## Author

**json-schema-2-markdown** © [ULIVZ](https://github.com/ulivz), Released under the [MIT](./LICENSE) License.<br>


> [github.com/ulivz](https://github.com/ulivz) · GitHub [@ULIVZ](https://github.com/ulivz) · Twitter [@_ulivz](https://twitter.com/_ulivz)


