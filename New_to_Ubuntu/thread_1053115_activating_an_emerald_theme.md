---
title: "activating an emerald theme"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by libihero on 2009-01-28
i have ubuntu 8.10 and i downloaded emerald with some themes.  i imported the themes onto emerald, but i dunno how to activate them.  i click on them and nothing happens

---

### Post by SunnyRabbiera on 2009-01-28
Well the next thing you can do is to install compizconfig-settings-manager, after that run the new app and under window decorations put this in:
emerald --replace in the box that says "command" next to it.
log out and it should work.

---

### Post by Sub101 on 2009-01-28
You need to run:

```
emerald --replace
```

Most users add this to their start up programs in sessions. Otherwise you would need to manually run the command each time.

---

