## I vibecoded this with Multisynq

[![npm version](https://img.shields.io/npm/v/@multisynq/client)](https://www.npmjs.com/package/@multisynq/client)
[![bundle size](https://img.shields.io/bundlephobia/minzip/@multisynq/client)](https://www.npmjs.com/package/@multisynq/client)
[![license](https://img.shields.io/npm/l/@multisynq/client)](https://github.com/Multisynq/client/blob/main/LICENSE)

## Quickstart

```bash
npm install @multisynq/client
```

```html
<!-- or include via CDN -->
<script src="https://cdn.jsdelivr.net/npm/@multisynq/client@1.0.2/bundled/multisynq-client.min.js"></script>
```

```js
import { Session, Model, View } from '@multisynq/client';

class MyModel extends Model {
  init() {
    this.state = { count: 0 };
  }
  increment() {
    this.state.count++;
  }
}

class MyView extends View {
  onRender() {
    this.root.innerHTML = `
      <button id="inc">+</button>
      <span>${this.model.state.count}</span>
    `;
    this.root.querySelector('#inc')
      .addEventListener('click', () => this.publish('increment'));
    this.subscribe('increment', () => this.render());
  }
}

Session.join({ apiKey: process.env.SYNQ_KEY, model: MyModel })
  .then(session => new MyView(session))
  .catch(console.error);
```

> Read the full docs at [multisynq.io/docs](https://multisynq.io/docs) and check out examples on [GitHub](https://github.com/Multisynq)  
> Drop your code and snag a free SYNQ_KEY at [multisynq.io](https://multisynq.io)  
