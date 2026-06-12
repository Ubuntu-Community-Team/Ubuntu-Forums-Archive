---
title: "Can't Install via Terminal"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-05-03
I am trying to install something in my terminal (ubuntu 10.04) and everytime I try to do this I get this error at the bottome:

```
W: Failed to fetch http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

```

I have removed all the gloobus repos from my software sources and I still get the same issue.

How do I remedy this?  It is freaking annoying.

---

### Post by mbzn on 2010-05-03
Seems like the server is offline or your net conection isn't stable. What happens when you "ping http://ppa.launchpad.net/" (press Ctrl-d to stop)

---

### Post by WinterRain on 2010-05-03
Did you remove the gloobus repos via gui or gedit?

---

### Post by Dobbie03 on 2010-05-03
> **mbzn said:**
> Seems like the server is offline or your net conection isn't stable. What happens when you "ping http://ppa.launchpad.net/" (press Ctrl-d to stop)

This is the reuslt

> ping: unknown host [http://ppa.launchpad.net/](http://ppa.launchpad.net/)


@ WinterRain

I removed via gui.

---

### Post by WinterRain on 2010-05-03
Do:
```
gksudo gedit /etc/apt/sources.list
```
and manually remove any references to gloobus. (remove the line)
then *sudo apt-get update*.

---

### Post by Dobbie03 on 2010-05-03
> **WinterRain said:**
> Do:
```
gksudo gedit /etc/apt/sources.list
```
and manually remove any references to gloobus. (remove the line)
then *sudo apt-get update*.

Thanks WinterRain, worked perfect!

---

