---
title: "[Kubuntu]Konsole global command to start new tab"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Aparthia on 2010-07-13
Hello there.

I'm a relatively new user to (k)ubuntu and I have a problem that I can't seem to solve.
I want to make a shortcut to Konsole, like the shortcut I had in ubuntu(super-t for terminal) and I got that figured out using input actions found using alt-F2. 

The problem that arises now, is that I don't want to run several Konsoles at any given time and I therefore use tabs within one Konsole app, and I wondered if there was any way to make a script that started Konsole, if none was active, and made a tab afterwards using the same hotkey if Konsole is started.

I have found the way to make a new tab konsole --new-tab, but I can't figure out how to put konsole / konsole --new-tab into one command. This leads me to my question: Do any of you know how to do this?

---

### Post by RiceMonster on 2010-07-13
Something like this might work (I can't test it right now, unfotunately):

```
#!/bin/bash

if ps aux | grep -v grep | grep konsole
    konsole --new-tab
else
    konsole
fi
```

---

### Post by Aparthia on 2010-07-13
> **RiceMonster said:**
> Something like this might work (I can't test it right now, unfotunately):

```
#!/bin/bash

if ps aux | grep -v grep | grep konsole
    konsole --new-tab
else
    konsole
fi
```

When I try to run that script in Konsole it says that the argument else is invalid : /

---

### Post by RiceMonster on 2010-07-13
```
#!/bin/bash

if ps aux | grep -v grep | grep konsole
then
    konsole --new-tab
else
    konsole
fi
```

Try it like that.

---

### Post by Aparthia on 2010-07-13
> **RiceMonster said:**
> [code]Try it like that.

It works flawlessly, thanks!

---

### Post by RiceMonster on 2010-07-13
Glad to help :)

---

