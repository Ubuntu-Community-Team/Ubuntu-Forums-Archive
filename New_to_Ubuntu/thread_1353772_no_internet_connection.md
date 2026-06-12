---
title: "no internet connection"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by joost0 on 2009-12-13
I've installed Ubuntu 9.10 on one of my pc's. Everything went ok, except that I don't have an internet connection.
I have a wired ADSL internet connection.
Networkadapter: VIA VT6105 Rhine III Fast Ethernet Adapter.
PC: Gateway G6-400.
I noticed that the network device is lo. (Whatever that may be).
I have no experience with linux.

---

### Post by ikt on 2009-12-13
> **joost0 said:**
> I've installed Ubuntu 9.10 on one of my pc's. Everything went ok, except that I don't have an internet connection.

Heya welcome to the land of linux! though I must admit this is an awfully bad start, every ubuntu installation I've done so far (hundreds) has had ethernet/internet working from the start. :/ 

> 
I noticed that the network device is lo. (Whatever that may be).
I have no experience with linux.

lo is basically a local connection, ie refers to itself, it's on every machine.

> I have a wired ADSL internet connection.
Networkadapter: VIA VT6105 Rhine III Fast Ethernet Adapter.
PC: Gateway G6-400.

The problem appears to be that the network hardware is not compatible with the latest versions of linux.

If you have a spare network card lying around try using that instead.

The other option is trying ubuntu 8.04, some people are suggesting it works on that, but I would just grab a $5 network card.

---

### Post by singfoo on 2009-12-13
There is a problem with 9.10 in dealing with adsl connections. There is a bug in network manager.  The fix is complex for a noobie.  My advice for you is reinstall with 9.04 and not use 9.10.  Many new stuff in 9.10 is not great for noobies...like grub2, exf4, etc. 
If you are willing to learn.  Then search the forum for the fix and learn all about ubuntu.  The folks here are great.

---

### Post by woodnymph on 2009-12-13
ditto on trying 8.04.  also, 8.04 will be able to upgrade to 10.04 in april ..

---

