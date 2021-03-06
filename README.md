# koa-prometheus

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]

## Installation

```sh
npm install -i koa-prometheus prom-client
```
## Usage

Complete example 😀

```js
const koa = require('koa');
const prom = require('prom-client');
const koaPrometheus = require('koa-prometheus');

const app = new Koa();


app.use(koaPrometheus.DefaultHTTPMetricsInjector(prom.registry))
    .use(async (ctx) => {
        if(ctx.request.method === 'GET' && ctx.request.url === '/metrics') {
            return await koaPrometheus.metricsHandler(ctx);
        }

        ctx.status = 200;
        ctx.body = 'koa 💛 prometheus';
    })
```

# License 

MIT

[npm-image]: https://img.shields.io/npm/v/koa-prometheus-adv.svg?style=flat-square
[npm-url]: https://www.npmjs.com/package/koa-prometheus-adv
[travis-image]: https://img.shields.io/pastjean/koa-prometheus/koa/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/pastjean/koa-prometheus
