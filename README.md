# @skaldapp/milkdown-nodes

Custom nodes and schema extensions for [Milkdown](https://milkdown.dev/), a block-style rich text editor framework.

## Installation

```bash
npm install @skaldapp/milkdown-nodes
```

## Usage

### HTML Schema with Syntax Highlighting

The package provides an extended HTML schema that adds syntax-highlighted code blocks using [Prism.js](https://prismjs.com/).

```typescript
import { htmlSchemaExtended } from "@skaldapp/milkdown-nodes";

// Use with your Milkdown editor setup
import { Editor, rootCtx } from "@milkdown/core";
import { commonmark } from "@milkdown/preset-commonmark";

const editor = Editor.create()
  .config((ctx) => {
    ctx.set(rootCtx, document.getElementById("editor"));
  })
  .use(commonmark)
  .use(htmlSchemaExtended);
```

### What It Does

The `htmlSchemaExtended` extends Milkdown's base HTML schema from the CommonMark preset with the following enhancements:

- **Syntax Highlighting**: HTML code blocks are rendered with Prism.js syntax highlighting
- **Custom Attributes**: Adds `data-type` and `data-value` attributes to HTML nodes
- **Inline Display**: Wraps HTML code in an inline-block span element

### Example Output

When rendering HTML code, the output will be:

```html
<span class="inline-block" data-type="html" data-value="<div>example</div>">
  <code class="language-html">
    <!-- Syntax-highlighted HTML code -->
  </code>
</span>
```

## API

### Exports

| Export               | Description                                           |
| -------------------- | ----------------------------------------------------- |
| `htmlSchemaExtended` | Extended HTML schema with syntax highlighting support |

## Dependencies

| Package         | Version | Purpose                             |
| --------------- | ------- | ----------------------------------- |
| `@milkdown/kit` | ^7.19.0 | Milkdown editor framework           |
| `prismjs`       | ^1.30.0 | Syntax highlighting for code blocks |

## Development

### Prerequisites

- Node.js (compatible with project requirements)
- npm

### Setup

```bash
# Install dependencies
npm install
```

### Commands

```bash
# Build the project
npm run build

# Run linting
npm run lint
```

### Project Structure

```
milkdown-nodes/
├── src/
│   ├── index.ts          # Main entry point
│   └── schemas/
│       └── html.ts       # HTML schema extension
├── dist/                 # Compiled output
├── package.json
├── tsconfig.json
└── eslint.config.ts
```

## License

[AGPL-3.0-or-later](LICENSE)

## Author

Jerry Bruwes <jbruwes@gmail.com>

## Links

- [GitHub Repository](https://github.com/skaldapp/milkdown-nodes)
- [Issues](https://github.com/skaldapp/milkdown-nodes/issues)
- [Milkdown Documentation](https://milkdown.dev/)
- [Prism.js Documentation](https://prismjs.com/)
