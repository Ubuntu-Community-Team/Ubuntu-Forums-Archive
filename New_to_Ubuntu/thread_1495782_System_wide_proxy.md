---
title: "System wide proxy?"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by Lord.Quackstar on 2010-05-28
I've tried to set a system proxy for when I join a certain network in lubuntu, but I'm forced to set it per application (IE Google Chrome). Is there a proxy configurer for lubuntu like in Gnome?

---

### Post by areskz on 2010-06-06
You can launch Chromium behind a proxy by adding one line to it's launcher, located in /etc/chromium-browser/default

The line you need to add exports http_proxy variable.

export http_proxy="http://username:password@proxy:port/"

that worked for me.

---

### Post by cirobr on 2012-01-24
> **areskz said:**
> You can launch Chromium behind a proxy by adding one line to it's launcher, located in /etc/chromium-browser/default

The line you need to add exports http_proxy variable.

export http_proxy="http://username:password@proxy:port/"

that worked for me.

What it worked for me was a bit simpler, i.e., without the userid/password pair:

```
export http_proxy="http://proxy:port/"
```

as Google Chrome opens a small window for typing that info, once a web page is requested.

---

### Post by oldos2er on 2012-01-24
Closed, necromancy.

---

