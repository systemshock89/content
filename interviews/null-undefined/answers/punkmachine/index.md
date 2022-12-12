`null` обычно задаётся переменной явно и означает, что она ничего не содержит. `undefined` показывает, что значение переменной «не определено». `undefined` обычно присваивается переменной, когда она была объявлена, но не было определено её начальное значение. Также, `undefined` может возвращаться и из функции — это происходит, если функции явно не возвращает ничего другого. `null` же обычно возвращают из функции явно, чтобы показать, что результат функции равен «ничему».

Без начального значения можно оставлять только переменную объявленную через `let` или `var`. Если объявить переменную через `const` и не задать ей начального значения, будет ошибка: `Uncaught SyntaxError: Missing initializer in const declaration`.

Оператор `typeof` для `null` работает странно. `typeof(null)` выдаст нам строку *'object'*. Это официально признанная ошибка в языке, сохраняемая для совместимости. Ошибка тут в том, что `null` это отдельный тип данных, а не объект. С `undefined` всё куда лучше и `typeof(undefined)` выдаст нам *'undefined'*. Почитать ещё о `typeof` можно [здесь](/js/typecasting/#typeof).

Поговорим немного о [приведении типов](/js/typecasting/). Для начала, пример:

```js
console.log(null + null); // 0
console.log(undefined + undefined); // NaN
```

Почему так?

`null` во время сложения приводится к нулю. Это логично, так как числовым значением «ничего» является как раз 0.
С `undefined` другое поведении, так как JavaScript пытается привести его к числу, но у него не получается и в результате мы получаем `NaN`.

Немного упомяну и про оператор нулевого слияния (`??`). В выражении между двумя операндами, он будет возвращать первый операнд, если он не равен `null` или `undefined`. Можно сказать, что `??` приравнивает смысл `undefined` и `null` к «ничего не содержит» и в этом случае, кладёт в переменную значение второго операнда.