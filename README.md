<h1 align="center">
Walrus ESLint 规则
</h1>

[![npm package](https://img.shields.io/npm/v/@walrus/eslint-config.svg)](https://www.npmjs.org/package/@walrus/eslint-config)
[![npm downloads](http://img.shields.io/npm/dm/@walrus/eslint-config.svg)](https://www.npmjs.org/package/@walrus/eslint-config)

> 如不使用walrus生态，请使用 [eslint-config-alloy](https://github.com/AlloyTeam/eslint-config-alloy)

## 规则列表

| 名称 | 包含规则 | 解析器 |
| --- | --- | --- |
| [标准规则](#标准规则) | [ESLint 规则][] | [babel-eslint][] |
| [React](#react) | ESLint 规则、[eslint-plugin-react][] | babel-eslint |
| [Vue](#vue) | ESLint 规则、[eslint-plugin-vue][] | [vue-eslint-parser][] |
| [TypeScript](#typescript) | ESLint 规则、[@typescript-eslint][] |[@typescript-eslint/parser][] |
| [TypeScript React](#typescript-react) | ESLint 规则、@typescript-eslint、eslint-plugin-react | @typescript-eslint/parser |
| TypeScript Vue（开发中） | | |

[babel-eslint]: https://github.com/babel/babel-eslint
[vue-eslint-parser]: https://github.com/mysticatea/vue-eslint-parser
[@typescript-eslint/parser]: https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/parser
[ESLint 规则]: https://eslint.org/docs/rules/
[eslint-plugin-react]: https://github.com/yannickcr/eslint-plugin-react
[eslint-plugin-vue]: https://eslint.vuejs.org/rules/
[@typescript-eslint]: https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin#supported-rules

## 配置原则

我们依据以下三条原则，研读了 ESLint 所有的配置项，定制出了心目中的「完美」ESLint 配置。

1. 能够帮助发现代码错误的规则，全部开启
2. 配置不应该依赖于某个具体项目，而应该全局合理
3. 帮助保持团队的代码风格统一，而不是限制开发体验

## 配置解读

ESLint 的配置多达几百条，逐个查阅是一项非常繁重的工作，我们为了简化个性化配置的成本，针对每一条配置都有一句话的注释，以及对应的错误示例和正确示例。这样不仅方便了我们自己查阅某项配置的意义和原因，也使大家更容易配置出自己心目中的规则：

- 每一条配置都有一句话注释说明此配置的用途
- 每个开启的配置都有对应的错误示例和正确示例
- 每个示例都会在真实的 ESLint 脚本中运行，以保证报错项与配置一一匹配
- 对于有争议的配置，都在注释中说明了为什么要这么配置的原因
- 样式相关的规则交给更专业的 [Prettier](https://prettier.io/) 处理

## 使用方法

### 标准规则

安装：

```bash
npm install --save-dev eslint babel-eslint @walrus/eslint-config
```

在你的项目根目录下创建 `.eslintrc.js`，并将以下内容复制到文件中：

```js
module.exports = {
    extends: [
        '@walrus/eslint-config',
    ],
    env: {
        // 这里填入你的项目用到的环境
        // 它们预定义了不同环境的全局变量，比如：
        //
        // browser: true,
        // node: true,
        // mocha: true,
        // jest: true,
        // jquery: true
    },
    globals: {
        // 这里填入你的项目需要的全局变量
        // false 表示这个全局变量不允许被重新赋值，比如：
        //
        // myGlobal: false
    },
    rules: {
        // 这里填入你的项目需要的个性化配置
    }
};
```

### React

安装：

```bash
npm install --save-dev eslint babel-eslint eslint-plugin-react @walrus/eslint-config
```

在你的项目根目录下创建 `.eslintrc.js`，并将以下内容复制到文件中：

```js
module.exports = {
    extends: [
        '@walrus/eslint-config',
        '@walrus/eslint-config/react',
    ],
    env: {
        // 这里填入你的项目用到的环境
        // 它们预定义了不同环境的全局变量，比如：
        //
        // browser: true,
        // node: true,
        // mocha: true,
        // jest: true,
        // jquery: true
    },
    globals: {
        // 这里填入你的项目需要的全局变量
        // false 表示这个全局变量不允许被重新赋值，比如：
        //
        // myGlobal: false
    },
    rules: {
        // 这里填入你的项目需要的个性化配置
    }
};
```

### Vue

安装：

```bash
npm install --save-dev eslint babel-eslint vue-eslint-parser@5.0.0 eslint-plugin-vue @walrus/eslint-config
```

注意：由于[这个原因](https://github.com/mysticatea/vue-eslint-parser/issues/46)，不能使用最新版的 vue-eslint-parser，必须使用 5.0.0 版本。

在你的项目根目录下创建 `.eslintrc.js`，并将以下内容复制到文件中：

```js
module.exports = {
    extends: [
        '@walrus/eslint-config',
        '@walrus/eslint-config/vue',
    ],
    env: {
        // 这里填入你的项目用到的环境
        // 它们预定义了不同环境的全局变量，比如：
        //
        // browser: true,
        // node: true,
        // mocha: true,
        // jest: true,
        // jquery: true
    },
    globals: {
        // 这里填入你的项目需要的全局变量
        // false 表示这个全局变量不允许被重新赋值，比如：
        //
        // myGlobal: false
    },
    rules: {
        // 这里填入你的项目需要的个性化配置
    }
};
```

### TypeScript

安装：

```bash
npm install --save-dev eslint typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin @walrus/eslint-config
```

在你的项目根目录下创建 `.eslintrc.js`，并将以下内容复制到文件中：

```js
module.exports = {
    extends: [
        '@walrus/eslint-config',
        '@walrus/eslint-config/typescript',
    ],
    env: {
        // 这里填入你的项目用到的环境
        // 它们预定义了不同环境的全局变量，比如：
        //
        // browser: true,
        // node: true,
        // mocha: true,
        // jest: true,
        // jquery: true
    },
    globals: {
        // 这里填入你的项目需要的全局变量
        // false 表示这个全局变量不允许被重新赋值，比如：
        //
        // myGlobal: false
    },
    rules: {
        // 这里填入你的项目需要的个性化配置
    }
};
```

### TypeScript React

安装：

```bash
npm install --save-dev eslint typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-react @walrus/eslint-config
```

在你的项目根目录下创建 `.eslintrc.js`，并将以下内容复制到文件中：

```js
module.exports = {
    extends: [
        '@walrus/eslint-config',
        '@walrus/eslint-config/react',
        '@walrus/eslint-config/typescript',
    ],
    env: {
        // 这里填入你的项目用到的环境
        // 它们预定义了不同环境的全局变量，比如：
        //
        // browser: true,
        // node: true,
        // mocha: true,
        // jest: true,
        // jquery: true
    },
    globals: {
        // 这里填入你的项目需要的全局变量
        // false 表示这个全局变量不允许被重新赋值，比如：
        //
        // myGlobal: false
    },
    rules: {
        // 这里填入你的项目需要的个性化配置
    }
};
```

## Troubleshootings

### 在 VSCode 中使用

在 VSCode 中，默认 ESLint 并不能识别 `.vue`、`.ts` 或 `.tsx` 文件，需要在「文件 => 首选项 => 设置」里做如下配置：

```json
{
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        "vue",
        "typescript",
        "typescriptreact"
    ]
}
```

### VSCode 中的 autoFixOnSave 没有效果

如果需要针对 `.vue`、`.ts` 和 `.tsx` 文件开启 ESLint 的 autoFix，则需要配置成：

```json
{
    "eslint.autoFixOnSave": true,
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        {
            "language": "vue",
            "autoFix": true
        },
        {
            "language": "typescript",
            "autoFix": true
        },
        {
            "language": "typescriptreact",
            "autoFix": true
        }
    ]
}
```

### 如何结合 Prettier 使用

Walrus ESLint 规则不包含所有样式相关的规则。只需要安装 `prettier` 及相关 VSCode 插件即可。

下面给出一个 Walrus 使用的 `prettier.config.js` 配置，仅供参考：

```js
// prettier.config.js or .prettierrc.js
module.exports = {
    // 一行最多 100 字符
    printWidth: 100,
    // 使用 2 个空格缩进
    tabWidth: 2,
    // 不使用缩进符，而使用空格
    useTabs: false,
    // 行尾需要有分号
    semi: true,
    // 使用单引号
    singleQuote: true,
    // 对象的 key 仅在必要时用引号
    quoteProps: 'as-needed',
    // jsx 不使用单引号，而使用双引号
    jsxSingleQuote: false,
    // 末尾不需要逗号
    trailingComma: 'none',
    // 大括号内的首尾需要空格
    bracketSpacing: true,
    // jsx 标签的反尖括号需要换行
    jsxBracketSameLine: false,
    // 箭头函数，只有一个参数的时候，也需要括号
    arrowParens: 'always',
    // 每个文件格式化的范围是文件的全部内容
    rangeStart: 0,
    rangeEnd: Infinity,
    // 不需要写文件开头的 @prettier
    requirePragma: false,
    // 不需要自动在文件开头插入 @prettier
    insertPragma: false,
    // 使用默认的折行标准
    proseWrap: 'preserve',
    // 根据显示样式决定 html 要不要折行
    htmlWhitespaceSensitivity: 'css',
    // 换行符使用 lf
    endOfLine: 'lf'
};
```

## Testing

```bash
npm test
```

## Contributing

为了实现高度自动化，此项目的整体架构如下：

- 所有 ESLint 配置均在 `test` 目录下
- 每一项配置存放在对应的目录下，如 `test/react/jsx-key/.eslintrc.js` 描述了规则 `react/jsx-key`
- 如果配置开启了，则需要有对应的示例，包括 `bad.js` 和 `good.js`
- 由于配置和示例在一个目录下，故编辑器中可以直接看到错误信息
- 由 `scripts/build.ts` 脚本将 `test` 目录下分散的配置生成整体的配置
- 运行测试脚本 `test/index.ts` 会检查每个示例是否按照要求报错

### 常用命令

```bash
# 安装依赖
npm i
# 构建 index.js react.js 等 eslintrc 配置
npm run build
# 执行测试
npm test
# 自动修复 ESLint 错误
npm run eslint:fix
# 自动修复格式错误
npm run prettier:fix
# 发布新版本
npm version <major|minor|patch>
git push --follow-tags
npm publish
```
