---
layout: page
title: Cloud Providers | Integration | PM2 Documentation
menu: starter
lang: en
section: process-manager
redirect_from: "/process-manager/integration/cloud-providers"
---

# Using PM2 in a Cloud Provider

You might find yourself in a situation in which you do not have access to the CLI to start your Node.js applications.

In such a situation, pm2 must be added as a dependency and must be called with the start script.

---

## Prepare your app

### Set your ecosystem file

Generate an `ecosystem.config.js` template with:

```bash
pm2 init
```

Modify the ecosystem file to match your needs:

```javascript
module.exports = {
  apps : [{
    name: "app",
    script: "./app.js",
    env: {
      NODE_ENV: "development",
    },
    env_production: {
      NODE_ENV: "production",
    }
  }]
}
```

?> Learn more about ecosystem file [here]({{ site.baseurl }}{% link en/process-manager/guide/ecosystem-file.md %}).

### Add PM2 as a module

Add pm2 as a dependency to your projet.

With npm:

```bash
npm install --save pm2
```

With yarn:

```bash
yarn add pm2
```

### Start script in package.json

In your `package.json`, modify your `start` script like the following:

```json
{
  "scripts": {
    "start": "node ./node_modules/.bin/pm2-runtime start ecosystem.config.js --env production"
  }
```

---

## Deploy your app

You can now deploy your application in your cloud providers like you would have done for a regular node.js app.

---

## Next step

Complete your configuration with the [Ecosystem File]({{ site.baseurl }}{% link en/process-manager/guide/ecosystem-file.md %})

Monitor your app on a web dashboard, with [Keymetrics]({{ site.baseurl }}{% link en/plus/integration/cloud-providers.md %})

---

## Questions ?

We are always happy to help with questions you might have. Search our documentation or check out answers to common questions. You can also post questions or comments to our community forum.
