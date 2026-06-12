---
title: "wired"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by dzon65 on 2010-02-19
My wired connecrtion's suddenly gone (can't find any connections).Plugged the cable in the pc next to it,and it works  okay.Anyone an idea?

---

### Post by Sef on 2010-02-19
1) Use a Live CD and see if it works.

a) Works - then software problem.
b) Does not work - hardware problem.

2) Plug your computer into the cable next to yours and see if it works. 

a) Works - then cable/connection problem.
b) Does not work - computer problem

---

### Post by dzon65 on 2010-02-19
When plugged in in the other pc itworks.

---

### Post by alphacrucis2 on 2010-02-19
> **dzon65 said:**
> When plugged in in the other pc itworks.

What output do you get from the following:

```
sudo ethtool eth0
```

---

### Post by dzon65 on 2010-02-19
That's "ethtool"? When I type it in>ther's no such command.

---

### Post by dzon65 on 2010-02-19
Btw.This happened after the pc was unwired for a couple of hours.The pc was on but not wired.

---

### Post by alphacrucis2 on 2010-02-19
> **dzon65 said:**
> That's "ethtool"? When I type it in>ther's no such command.

I guess you don't have the ethtool package installed. You can get it from the package manager but that's not much help with no network available. I find it quite useful as it tells you the link status among other things. 


What do these show:

```
ifconfig
```
```
route -n
```
```
cat /etc/resolv.conf
```

---

### Post by llamabr on 2010-02-19
No, ethtool should be installed by default.

type the actual command, using tab completion, and then copy the actual error message.

---

### Post by alphacrucis2 on 2010-02-19
> **llamabr said:**
> No, ethtool should be installed by default.

type the actual command, using tab completion, and then copy the actual error message.

Come to think of it I don't ever recall manually installing it, so you are right. It should be in the standard install. As you have surmised, perhaps the OP is typing something wrong.

---

### Post by dzon65 on 2010-02-19
Guys!Turned out a bunch was wrong,no shutdown/logout..............had to do a reinstall.Having a lot of problems lately.As for ethtool,it wasn't installed before,never had any troubles.This isn't a full install,a minimal.
Well,seems I bothered you for nothing.Don't know what went wrong with the machine.
Anyway,thanks for all the replies and I'll consider this solved.
Kind regards,J.

---

