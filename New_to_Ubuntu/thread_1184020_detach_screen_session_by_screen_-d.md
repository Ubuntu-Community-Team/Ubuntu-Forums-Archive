---
title: "detach screen session by screen -d"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by flylehe on 2009-06-10
Hi,
I was downloading something under a screen session on a server when my wireless connection stopped. When I reconnect to my server again, and the session was still shown as attached. So I tried to detach it first by:
```

screen -d downloadsession

```
However it has not responded for a long time since then. How could I detach and reattach to it?
Thanks!

---

### Post by MrWES on 2009-06-10
> **flylehe said:**
> Hi,
I was downloading something under a screen session on a server when my wireless connection stopped. When I reconnect to my server again, and the session was still shown as attached. So I tried to detach it first by:
```

screen -d downloadsession

```
However it has not responded for a long time since then. How could I detach and reattach to it?
Thanks!

What is the output of 
```
screen -list
```

~Bill

---

