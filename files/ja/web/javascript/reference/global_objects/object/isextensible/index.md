---
title: Object.isExtensible()
slug: Web/JavaScript/Reference/Global_Objects/Object/isExtensible
tags:
  - ECMAScript 5
  - JavaScript
  - JavaScript 1.8.5
  - Method
  - Object
translation_of: Web/JavaScript/Reference/Global_Objects/Object/isExtensible
---
{{JSRef}}

**`Object.isExtensible()`** メソッドは、オブジェクトが拡張可能であるか (新しいプロパティを追加することができるかどうか) を判定します。

{{EmbedInteractiveExample("pages/js/object-isextensible.html")}}

## 構文

```
Object.isExtensible(obj)
```

### 引数

- `obj`
  - : チェックするオブジェクトです。

### 返値

{{jsxref("Boolean")}} で、与えられたオブジェクトが拡張可能であるかどうかを示します。

## 解説

オブジェクトは既定では拡張可能です。つまり、新しいプロパティの追加が可能であり、 ({{jsxref("Object.proto", "__proto__")}} のプロパティに対応しているエンジンでは) `__proto__` プロパティを変更することができます。オブジェクトは {{jsxref("Object.preventExtensions()")}}, {{jsxref("Object.seal()")}}, {{jsxref("Object.freeze()")}} の何れかを用いる事で拡張不能に設定する事が可能です。

## 例

### Object.isExtensible の使用

```js
// 新規のオブジェクトは拡張可能
var empty = {};
Object.isExtensible(empty); // === true

// その設定は変える事が可能
Object.preventExtensions(empty);
Object.isExtensible(empty); // === false

// seal メソッドで封印されたオブジェクトは拡張不可と定義される
var sealed = Object.seal({});
Object.isExtensible(sealed); // === false

// freeze メソッドで凍結されたオブジェクトも拡張不可と定義される
var frozen = Object.freeze({});
Object.isExtensible(frozen); // === false
```

### オブジェクト以外の型強制

ES5 では、このメソッドの引数がオブジェクトではない場合 (プリミティブの場合)、 {{jsxref("TypeError")}} が発生します。 ES2015 以降では、オブジェクトでない引数は、それが拡張不可能な通常のオブジェクトであるかのように扱われ、単に `false` を返します。

```js
Object.isExtensible(1);
// TypeError: 1 is not an object (ES5 code)

Object.isExtensible(1);
// false                         (ES2015 code)
```

## 仕様書

| 仕様書                                                                                               |
| ---------------------------------------------------------------------------------------------------- |
| {{SpecName('ESDraft', '#sec-object.isextensible', 'Object.isExtensible')}} |

## ブラウザーの互換性

{{Compat("javascript.builtins.Object.isExtensible")}}

## 関連情報

- {{jsxref("Object.preventExtensions()")}}
- {{jsxref("Object.seal()")}}
- {{jsxref("Object.isSealed()")}}
- {{jsxref("Object.freeze()")}}
- {{jsxref("Object.isFrozen()")}}
- {{jsxref("Reflect.isExtensible()")}}
