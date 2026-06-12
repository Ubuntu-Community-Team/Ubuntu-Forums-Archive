---
title: "PSLB1A-02D008 Ubuntu 9.10 Drivers"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Skyxz on 2010-03-06
Hey all, second and last, and most important question i have for today.

I run a Satellite Pro L300; Model No. PSLB1A-02D008; Running Ubuntu 9.10; With wireless Realtek RTL8187B, I'd like to know how to get the drivers? i know the site to download them from, but they don't have any for Linux/Ubuntu, can i use ndiswrapper or whatever it's called, to install the drivers using the WinXP drivers?

if so, how would i install this ndiswrapper?
And how would i install the driver?

It's not alot to ask, but i'd appreciate this alot. Thanks!

---

### Post by patchwork on 2010-03-06
I've never had the need to use ndiswrapper, but you can get it from the repos:

```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
and, apparently there is an optional gui frontend
```
sudo apt-get install ndisgtk
```

Sorry I can't be of more help

---

