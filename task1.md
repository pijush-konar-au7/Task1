## Task 1 : Provide some example of config file separation for dev and prod environments.

### A configuration setup should have the following to keep it all perfect -

- The keys can be read from file & from the environment variables.
- To keep the secrets intact, it is kept outside of the committed code
- config file is hierarchical for easier findability.

### For example the following config file -

```sh
var config = {
  production: {
    mongo : {
      billing: '****'
    }
  },
  default: {
    mongo : {
      billing: '****'
    }
  }
}

exports.get = function get(env) {
  return config[env] || config.default;
}
```


### It uses the following -

```sh
const config = require('./config/config.js').get(process.env.NODE_ENV);
const dbConnection = mongoose.createConnection(config.mongo.billing);
```
