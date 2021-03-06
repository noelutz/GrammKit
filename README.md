# GrammKit

GrammKit is a tool for generating syntax diagrams (also known as railroad diagrams) for parser grammars. Check out the [online version](http://dundalek.com/GrammKit/).

Currently two grammar formats are supported:
- [PEG.js](http://pegjs.org) - it is parsed into internal AST of PEG.js which is then translated using [peg-rd.js](./lib/peg-rd.js).
- [EBNF](http://www.w3.org/TR/2004/REC-xml11-20040204/#sec-notation) defined in W3C standards - it parsed into AST using [parse-ebnf.pegjs](./lib/parse-ebnf.pegjs)
- [Ohm](https://github.com/harc/ohm) support is in progress. Translation will be done using semantic actions in [ohm-rd.js](./lib/ohm-rd.js)

Is uses the [railroad-diagrams](https://github.com/tabatkins/railroad-diagrams) library to generate SVG images.

## Use the command line utility

`npm install -g grammkit`

To generate static html page run `grammkit yourgrammar.peg`.

To generate markdown file run `grammkit -t md yourgrammar.peg`.
This will generate separate SVG files and a markdown file that includes them.

## Use the library

`npm install grammkit`

```javascript
var grammkit = require('grammkit');
var parse = require('pegjs/lib/parser').parse;

var grammar = parse('start = left ("+" / "-") right');
grammkit.diagram(grammar.rules[0]);
// => '<svg>...</svg>'

```

The SVG renders as:

![Diagram Example](example.png)

## Related projects

List of other project worth checking out.

- [jison debugger](http://nolanlawson.github.io/jison-debugger/) - interesting visualization of a parse tree for jison grammars
- [ohm interactive editor](https://ohmlang.github.io/editor/) - online editor for ohm grammars that also visualizes parse tree
