# Discordeno

<img align="right" src="https://raw.githubusercontent.com/discordeno/discordeno/main/site/static/img/logo.png" height="150px">

Discord API library for [Node.JS](https://nodejs.org), [Deno](https://deno.land) & [Bun](https://bun.sh/)

[![Discord](https://img.shields.io/discord/785384884197392384?color=7289da&logo=discord&logoColor=dark)](https://discord.com/invite/5vBgXk3UcZ)
[![codecov](https://codecov.io/gh/discordeno/discordeno/branch/main/graph/badge.svg?token=SQI9OYJ7AK)](https://codecov.io/gh/discordeno/discordeno)

## Tips

- If you are already convinced about using Discordeno, go to [Getting Started](https://discordeno.mod.land)
- To learn if Discordeno is right for you, read everything below.

## Packages

| Package                                                                  | npm                                                               | Tests                                                                                                                 | Coverage                                                                                                                                                            |
| ------------------------------------------------------------------------ | ----------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [discordeno](https://www.npmjs.com/package/discordeno)                   | ![npm (scoped)](https://img.shields.io/npm/v/discordeno)          | ![action status](https://github.com/discordeno/discordeno/actions/workflows/discordeno-test.yml/badge.svg?event=push) | [![codecov](https://codecov.io/gh/discordeno/discordeno/branch/main/graph/badge.svg?token=SQI9OYJ7AK&flag=discordeno)](https://codecov.io/gh/discordeno/discordeno) |
| [@discordeno/types](https://www.npmjs.com/package/@discordeno/types)     | ![npm (scoped)](https://img.shields.io/npm/v/@discordeno/types)   | ![action status](https://github.com/discordeno/discordeno/actions/workflows/types-test.yml/badge.svg?event=push)      | [![codecov](https://codecov.io/gh/discordeno/discordeno/branch/main/graph/badge.svg?token=SQI9OYJ7AK&flag=types)](https://codecov.io/gh/discordeno/discordeno)      |
| [@discordeno/utils](https://www.npmjs.com/package/@discordeno/utils)     | ![npm (scoped)](https://img.shields.io/npm/v/@discordeno/utils)   | ![action status](https://github.com/discordeno/discordeno/actions/workflows/utils-test.yml/badge.svg?event=push)      | [![codecov](https://codecov.io/gh/discordeno/discordeno/branch/main/graph/badge.svg?token=SQI9OYJ7AK&flag=utils)](https://codecov.io/gh/discordeno/discordeno)      |
| [@discordeno/rest](https://www.npmjs.com/package/@discordeno/rest)       | ![npm (scoped)](https://img.shields.io/npm/v/@discordeno/rest)    | ![action status](https://github.com/discordeno/discordeno/actions/workflows/rest-test.yml/badge.svg?event=push)       | [![codecov](https://codecov.io/gh/discordeno/discordeno/branch/main/graph/badge.svg?token=SQI9OYJ7AK&flag=rest)](https://codecov.io/gh/discordeno/discordeno)       |
| [@discordeno/gateway](https://www.npmjs.com/package/@discordeno/gateway) | ![npm (scoped)](https://img.shields.io/npm/v/@discordeno/gateway) | ![action status](https://github.com/discordeno/discordeno/actions/workflows/gateway-test.yml/badge.svg?event=push)    | [![codecov](https://codecov.io/gh/discordeno/discordeno/branch/main/graph/badge.svg?token=SQI9OYJ7AK&flag=gateway)](https://codecov.io/gh/discordeno/discordeno)    |
| [@discordeno/bot](https://www.npmjs.com/package/@discordeno/bot)         | ![npm (scoped)](https://img.shields.io/npm/v/@discordeno/bot)     | ![action status](https://github.com/discordeno/discordeno/actions/workflows/bot-test.yml/badge.svg?event=push)        | [![codecov](https://codecov.io/gh/discordeno/discordeno/branch/main/graph/badge.svg?token=SQI9OYJ7AK&flag=bot)](https://codecov.io/gh/discordeno/discordeno)        |

## Features

Discordeno is actively maintained to guarantee **excellent performance, latest features, and ease of use.**

- **Simple, Efficient, and Lightweight**: Discordeno is lightweight, simple to use, and adaptable.
  - By default: No caching.
- **Functional & Class API**: Discordeno is flexible enough to provide both methods.
  - The functional API eliminates the challenges of extending built-in classes and inheritance while ensuring overall simple but performant code.
  - The class based API, client package, provides a similar api as the [Eris](https://github.com/abalabahaha/eris) library to provide the best class based experience.
- **Cross Runtime**: Supports the Node.js, Deno, and Bun runtimes.
- **Standalone components**: Discordeno offers the option to have practically any component of a bot as a separate
  piece, including standalone REST, gateways, custom caches, and more.
- **Flexibility/Scalability:** Remove any properties, if your bot doesn't need them. For instance, remove `Channel.topic` if your bot doesn't require it. You may save GBs of RAM in this way. A few lines of code are all that are needed to accomplish this for any property on any object.

### REST

- Freedom from 1 hour downtimes due to invalid requests
  - Prevent your bot from being down for an hour, by lowering the maximum downtime to 10 minutes.
- Freedom from global rate limit errors
  - As a bot grows, you need to handle global rate limits better. Shards don't communicate fast enough to truly
    handle it properly. With one point of contact to discords API, you will never have issues again.
  - Numerous instances of your bot on different hosts, all of which can connect to the same REST server.
- REST does not rest!
  - Separate rest guarantees that your queued requests will continue to be processed even if your bot breaks for
    whatever reason.
  - Seamless updates! When updating/restarting a bot, you'll lose a lot of messages or replies that are queued/processing.
- Single point of contact to Discord API
  - Send requests from any location, even a bot dashboard directly.
  - Don't send requests from dashboard to bot process to send a request to discord. Your bot process should
    be freed up to handle bot events!
- Scalability! Scalability! Scalability!

### Gateway

- **Zero Downtime Updates:**
  - Others: With non-proxy bots, it takes about 5s per shard bucket to start up. With 100,000 servers, this would be minimum of 8+ minutes of downtime for bot updates.
  - Discordeno Proxy Gateway: Resume the bot code almost instantly without worrying about any delays or wasting your identify limits.
- **Zero Downtime Resharding:**
  - Discord stops allowing your bot to be added to new servers when you max out your existing max shards. Consider a bot started with 150 shards
    operating on 150,000 servers. Your shards support a maximum of 150 \* 2500 = 375,000 servers. Your
    bot will be unable to join new servers once it reaches this point until it re-shards.
  - DD proxy provides 2 types of re-sharding. Automated and manual. You can also have both.
    - Automated: This system will automatically begin a Zero-downtime resharding process behind the scenes when you
      reach 80% of your maximum servers allowed by your shards. For example, since 375,000 was the max, at 300,000 we
      would begin re-sharding behind the scenes with ZERO DOWNTIME.
      - 80% of maximum servers reached (The % of 80% is customizable.)
      - Identify limits have room to allow re-sharding. (Also customizable)
    - Manual: You can also trigger this manually should you choose.
      - When discord releases a new API version, updates your gateways to new version with no downtime.
- **Horizontal Scaling:**
  - When your bot grows a lot, you have
    two options: you can either keep investing money to upgrade your server or you may expand horizontally by purchasing
    several more affordable servers. The proxy enables WS handling on multiple servers.
- **No Loss Restarts:**
  - Without the proxy mechanism, you would typically lose a lot of events while restarting. Users could issue
    instructions or send messages that are not automoderated. As your bot grows, this amount grows sharply.
    Users who don't receive the automatic roles or any other activities your bot should do.
  - While your bot is unavailable, events can be added to a queue, and once the bot is back online, the queue will start processing all of the events.
- **Flexibility:**
  - You have complete control over everything inside the gateway thanks to the controller aspect. Need to customize, the way the manager talks to the workers? Simply, plug in and override the method.
- **Clustering With Workers:**
  - Utilize all of your CPU cores to their greatest potential by distributing the workload across workers. To enhance
    efficiency, manage how shards per worker.

### Custom Cache

Have your cache setup in any way you like. Redis, PGSQL or any cache layer you would like.

## Getting Started

Interested? [Check the website](https://discordeno.mod.land) for more details on getting started.

### Tools

This library is not intended for beginners, however if you still want to utilise it, check out these excellent official
and unofficial templates:

## Links

- [Website](https://discordeno.mod.land)
- [Documentation](https://doc.deno.land/https/deno.land/x/discordeno/mod.ts)
- [Discord](https://discord.com/invite/5vBgXk3UcZ)

Discordeno follows [semantic versioning](https://semver.org/)
