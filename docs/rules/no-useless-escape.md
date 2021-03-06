---
title: no-useless-escape - Rules
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Disallow unnecessary escape usage (no-useless-escape)

Escaping non-special characters in strings and regular expressions doesn't have any effects on results, as in the following example:

```js
let foo = "hol\a"; // > foo = "hola"
let bar = /\:/ // same functionality with /:/
```

## Rule Details

This rule flags escapes that can be safely removed without changing behavior.

The following patterns are considered problems:

```js
/*eslint no-useless-escape: "error"*/

"\'";
'\"';
"\#";
"\e";
/\!/;
/\@/;

```

The following patterns are not considered problems:

```js
/*eslint no-useless-escape: "error"*/

"\"";
'\'';
"\x12";
"\u00a9";
"\371";
"xs\u2111";
/\\/g;
/\t/g;
/\\w\\$\\*\\^\\./;

```

## When Not To Use It

If you don't want to be notified about unnecessary escapes, you can safely disable this rule.

## Version

This rule was introduced in ESLint 2.5.0.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-useless-escape.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-useless-escape.md)
