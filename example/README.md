# Welcome to gitbook-plugin-google-tongji-with-multiple-channel 👋

[![npm:version](https://img.shields.io/npm/v/gitbook-plugin-google-tongji-with-multiple-channel.svg)](https://www.npmjs.com/package/gitbook-plugin-google-tongji-with-multiple-channel)
[![npm:download](https://img.shields.io/npm/dt/gitbook-plugin-google-tongji-with-multiple-channel.svg)](https://www.npmjs.com/package/gitbook-plugin-google-tongji-with-multiple-channel)
[![npm:prerequisite](https://img.shields.io/badge/gitbook-*-blue.svg)](https://www.npmjs.com/package/gitbook-plugin-google-tongji-with-multiple-channel)
[![github:documentation](https://img.shields.io/badge/documentation-yes-brightgreen.svg)](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel#readme)
[![github:maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/graphs/commit-activity)
[![npm:license](https://img.shields.io/npm/l/gitbook-plugin-google-tongji-with-multiple-channel.svg)](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/blob/master/LICENSE)
[![github:snodreams1006](https://img.shields.io/badge/github-snowdreams1006-brightgreen.svg)](https://github.com/snowdreams1006)
[![微信公众号:雪之梦技术驿站-brightgreen.svg](https://img.shields.io/badge/%E5%BE%AE%E4%BF%A1%E5%85%AC%E4%BC%97%E5%8F%B7-%E9%9B%AA%E4%B9%8B%E6%A2%A6%E6%8A%80%E6%9C%AF%E9%A9%BF%E7%AB%99-brightgreen.svg)](https://snowdreams1006.github.io/snowdreams1006-wechat-public.jpeg)

> GitBook plugin that use Google Analytics to analyze website traffic, support for independent analysis of multiple channels, a source code deployed in multiple independent analysis.

## Preview

**Usage**

````json
{
    "plugins": [
        "google-tongji-with-multiple-channel"
    ],
    "pluginsConfig": {
        "google-tongji-with-multiple-channel": {
            "token": "UA-140787039-1"
        }
    }
}
````

**Result**

```js
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-140787039-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-140787039-1');
</script>
```

## Usage

### Step #1 - Update `book.json` file

In you gitbook's `book.json` file, add `google-tongji-with-multiple-channel` to `plugins` list.

Here is simplest example :

````json
{
    "plugins": [
        "google-tongji-with-multiple-channel"
    ],
    "pluginsConfig": {
        "google-tongji-with-multiple-channel": {
            "token": "UA-XXXX-Y"
        }
    }
}
````

In addition, the supported configuration options are as follows : 

```json
"gitbook": {
    "properties": {
        "token": {
            "description": "Google Analytics token",
            "required": false,
            "type": "string"
        },
        "url": {
            "description": "Google Analytics Url",
            "default": "https://www.googletagmanager.com/gtag/js",
            "required": false,
            "type": "string"
        },
        "multipleChannelConfig": {
            "description": "Google Analytics Multi-channel Configuration",
            "required": false,
            "type": "object"
        }
    }
}
```

### Step #2 - Run gitbook commands

- Run `gitbook install`. It will automatically install `google-tongji-with-multiple-channel` gitbook plugin for your book. This is needed only once.

```bash
gitbook install
```

or you can run `npm install gitbook-plugin-google-tongji-with-multiple-channel` to install locally.

```bash
npm install gitbook-plugin-google-tongji-with-multiple-channel
```

- Build your book (`gitbook build`) or serve (`gitbook serve`) as usual.

```bash
gitbook serve
```

### Step #3 - Verify that Google analysis code is injected

After uploading to the website, visit the homepage of the website to check whether the Google analysis script file is automatically injected. 

You can also check whether the configuration is successfully configured in the Google analysis background.

```js
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-140787039-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-140787039-1');
</script>
```

## Apply

### Step #1- Sign up for Google analytics

Visit the [Google analysis website](https://analytics.google.com/), register or log in the Google analysis account, click **create media resources** and fill in the relevant information of the website.

|name|demo|remark|
|:-:|:-:|:-:|
|name|`github`|required|
|website|`https://snowdreams1006.github.io/`|required|
|categories|`other`|required|
|timezone|`GMT+08:00`|optional|

### Step #2- Get the Google analysis code

After adding media resources successfully, click next to get the integration code script as follows:

```js
<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-140787039-1"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-140787039-1');
</script>
```

|name|demo|remark|
|:-:|:-:|:-:|
|`Source address`|`https://www.googletagmanager.com/gtag/js?id=UA-140787039-1`|`async`|
|`url`|`https://www.googletagmanager.com/gtag/js`|`Each site has the same value`|
|`token`|`UA-140787039-1`|`Each site has a google-tongji-with-multiple-channelerent value`|

### Step #3- Fill in the Google analysis configuration

Copy the token and url just applied and fill in the book.json configuration file, and fill in the Google analysis configuration information according to the actual situation.

- Single channel configuration only needs to fill in the value of `token`, the rest of the options are optional.

```json
"google-tongji-with-multiple-channel": {
  "token": "UA-140787039-1"
}
```

- In addition to filling in the value of `token` corresponding to the **website domain name**, multiple channels also need to fill in the Google analysis `url`

```json
"google-tongji-with-multiple-channel": {
    "url": "https://www.googletagmanager.com/gtag/js",
    "multipleChannelConfig": {
         "snowdreams1006.gitbook.io":{
            "token": "UA-140787039-1"
        },
        "snowdreams1006.github.io":{
            "token": "UA-140787039-2"
        },
        "snowdreams1006.gitee.io":{
            "token": "UA-140787039-3"
        },
        "snowdreams1006.gitlab.io":{
            "token": "UA-140787039-4"
        },
        "snowdreams1006.tech":{
            "token": "UA-140787039-5"
        },
        "blog.snowdreams1006.cn":{
            "token": "UA-140787039-6"
        }
    }
}
```

## Examples

- Official documentation configuration file

> [https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/blob/master/docs/book.json](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/blob/master/docs/book.json)

```json
{
    "plugins": ["google-tongji-with-multiple-channel"],
    "pluginsConfig": {
        "google-tongji-with-multiple-channel": {
            "multipleChannelConfig": {
                 "snowdreams1006.gitbook.io":{
                    "token": "UA-140787039-1"
                },
                "snowdreams1006.github.io":{
                    "token": "UA-140787039-2"
                },
                "snowdreams1006.gitee.io":{
                    "token": "UA-140787039-3"
                },
                "snowdreams1006.gitlab.io":{
                    "token": "UA-140787039-4"
                },
                "snowdreams1006.tech":{
                    "token": "UA-140787039-5"
                },
                "blog.snowdreams1006.cn":{
                    "token": "UA-140787039-6"
                }
            }
        }
    }
}
```

- Official example configuration file

> [https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/blob/master/example/book.json](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/blob/master/example/book.json)

```json
{
    "plugins": ["google-tongji-with-multiple-channel"],
    "pluginsConfig": {
        "google-tongji-with-multiple-channel": {
            "token": "UA-140787039-1"
        }
    }
}
```

**Note**: Above snippet can be used as complete `book.json` file, if your book doesn't have one yet.

## Thanks

- GitBook plugin for analytics purpose : [gitbook-plugin-analytics](https://github.com/YounGoat/gitbook-plugin-analytics)
- Google Analytics tracking for your book : [plugin-ga](https://github.com/GitbookIO/plugin-ga)
- A GitBook plug-in that supports multiple modules : [gitbook-plugin-devops](https://www.npmjs.com/package/gitbook-plugin-devops)

## Author

👤 **snowdreams1006**

- Website: [snowdreams1006.tech](https://snowdreams1006.tech/)
- Github: [@snowdreams1006](https://github.com/snowdreams1006)
- Email: [snowdreams1006@163.com](mailto:snowdreams1006@163.com)

## Contributing

Contributions, issues and feature requests are welcome! Feel free to check [issues page](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/issues).

## Show your support

Give a [Star](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel) if this project helped you!

![snowdreams1006-wechat-donate.jpg](https://snowdreams1006.github.io/snowdreams1006-wechat-donate.jpg)

## Copyright

Copyright © 2019 [snowdreams1006](https://github.com/snowdreams1006).

This project is [MIT](https://github.com/snowdreams1006/gitbook-plugin-google-tongji-with-multiple-channel/blob/master/LICENSE) licensed.