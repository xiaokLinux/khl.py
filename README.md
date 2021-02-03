# khl.py

SDK for kaiheila.cn in python

# install

Python requirement: >= Python 3.6

```shell
pip install khl.py
```

# quickly enroll

```python
import random

from khl import Bot, Cert

cert = Cert(client_id='xxxxxx', client_secret='xxxxxx', token='xxxxxx')
bot = Bot(cmd_prefix=['!', '！'], cert=cert)


@bot.command(name='roll')
async def roll(session):
    await session.reply(f'{random.randint(int(session.args[0]), int(session.args[1]))}')


bot.run()
# now invite the bot to ur server,
# and type '!roll 1 100'(in any channel) to check ur san today!
# (remember to grant read & send permissions to the bot first)
```

## notes for Mac OSX users:

if you encounter this error:

```
ssl.SSLCertVerificationError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed: unable to get local issuer certificate (_ssl.c:1123)
```

please install certi manually, turning to this post for guide:

[certificate verify failed: unable to get local issuer certificate](https://stackoverflow.com/a/58525755)

# short-term roadmap

## refactor

### T1:

- [ ] btn handler(ongoing)

### T2:

- [x] rename files according to PEP8
- [ ] wrap functions for convenient

## perf:

- [ ] refactor `Msg`, support multimedia msg (active @TWT233)
  - [x] introduce `MsgCtx` with this

## feat:

### T1:

- [x] `on_textMsg()`
- [ ] command & arg parse system(long term design needed)
- [x] event listener for bot
  - [x] find another approach to handle msg
  - [x] utilize event listener
- [x] add get for net client
- [x] command group
- [ ] event class(interface)

### T2:

- [x] log system
- [x] `MsgCtx` design
- [x] command alias
- [ ] bot send args (done by @fi6, waiting for merge)
- [ ] no prefix commands
- [ ] more kinds of msg

# commit message rules

only accept commits satisfying [Conventional Commits convention](https://github.com/commitizen/cz-cli)

search plugins with keyword `commitizen` for your editor/IDE, then addict to write commit message
