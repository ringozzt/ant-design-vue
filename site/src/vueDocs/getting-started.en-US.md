# Getting Started

Ant Design Vue is dedicated to providing a **good development experience** for programmers. Make sure that you had installed [Node.js](https://nodejs.org/)(> v8.9) correctly.

> Before delving into Ant Design Vue, a good knowledge base of [Vue](https://www.vuejs.org/) and [JavaScript ES2015](http://babeljs.io/docs/learn-es2015/) is needed.

## Playground

The following CodeSandbox demo is the simplest use case, and it's also a good habit to fork this demo to provide a re-producible demo while reporting a bug.

- [![Vue Antd Template](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/agitated-franklin-1w72v)

## Import ant-design-vue

### 1. Installation

[vue-cli](https://github.com/vuejs/vue-cli)

```bash
$ npm install -g @vue/cli
# OR
$ yarn global add @vue/cli
```

### 2. Create a New Project

A new project can be created using CLI tools.

```bash
$ vue create antd-demo
```

And, setup your vue project configuration.

### 3. Use antd's Components

#### Install

```bash
$ npm i --save ant-design-vue@next
```

#### Component Registration

If you use Vue's default template syntax, you need to register components before you can use them. There are three ways to register components:

**Global Registration All Components**

```jsx
import { createApp } from 'vue';
import Antd from 'ant-design-vue';
import App from './App';
import 'ant-design-vue/dist/antd.css';

const app = createApp(App);

app.use(Antd).mount('#app');
```

The above imports Antd entirely. Note that CSS file needs to be imported separately.

**Global Registration Some Components**

```jsx
import { createApp } from 'vue';
import { Button, message } from 'ant-design-vue';
import App from './App';

const app = createApp(App);

/* Automatically register components under Button, such as Button.Group */
app.use(Button).mount('#app');

app.config.globalProperties.$message = message;
```

**Local Registration**

In this way, component sub-components, such as Button and ButtonGroup, need to be registered separately, and they are only valid in the current component after registration. Therefore, we recommend using the above two methods.

```html
<template>
  <a-button>Add</a-button>
</template>
<script>
  import { Button } from 'ant-design-vue';
  const ButtonGroup = Button.Group;

  export default {
    components: {
      AButton: Button,
      AButtonGroup: ButtonGroup,
    },
  };
</script>
```

### 4. Component list

[Component list](https://github.com/vueComponent/ant-design-vue/blob/main/components/components.ts)

## Compatibility

Ant Design Vue 2.x supports all the modern browsers. If you want to use IE9+, you can use Ant Design Vue 1.x & Vue 2.x.

## Import on Demand

we can import individual components on demand:

```jsx
import Button from 'ant-design-vue/lib/button';
import 'ant-design-vue/lib/button/style'; // or ant-design-vue/lib/button/style/css for css format file
```

We strongly recommend using [babel-plugin-import](https://github.com/ant-design/babel-plugin-import), which can convert the following code to the 'ant-design-vue/lib/xxx' way:

```jsx
import { Button } from 'ant-design-vue';
```

And this plugin can load styles too, read [usage](https://github.com/ant-design/babel-plugin-import#usage) for more details.

> FYI, babel-plugin-import's `style` option will importing some global reset styles, don't use it if you don't need those styles. You can import styles manually via `import 'ant-design-vue/dist/antd.css'` and override the global reset styles.

If you use Vite, you can use [unplugin-vue-components](https://github.com/antfu/unplugin-vue-components) to load on demand. However, this plugin can only deal with components. Others such as message should be loaded manually:

```ts
import { message } from 'ant-design-vue';
import 'ant-design-vue/es/message/style/css'; //use ant-design-vue/es instead of ant-design-vue/lib
```

## Customization

- [Customize Theme](/docs/vue/customize-theme)
