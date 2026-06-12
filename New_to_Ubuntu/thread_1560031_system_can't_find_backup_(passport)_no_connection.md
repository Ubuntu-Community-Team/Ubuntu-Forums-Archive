---
title: "system can't find backup (passport) no connection"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by sewbiz on 2010-08-24
My passport can't be mounted. My computer does not see it. How can I fix this problem. I have Ubuntu - Jaunty...I think. I will have to check. Where do I find this?

---

### Post by tom.swartz07 on 2010-08-24
> **sewbiz said:**
> My passport can't be mounted. My computer does not see it. How can I fix this problem. I have Ubuntu - Jaunty...I think. I will have to check. Where do I find this?

Alrighty, lets get some diagnostics first.

Plug in your passport then Open a terminal (applications, accessories, terminal)
Type ```
lsusb
``` and copy/paste back what it spits back. 

This will list what devices you have plugged in and will help us determine if its a cable problem or a software problem.


Let us know! :D

---

### Post by sewbiz on 2011-06-11
> **tom.swartz07 said:**
> Alrighty, lets get some diagnostics first.

Plug in your passport then Open a terminal (applications, accessories, terminal)
Type ```
lsusb
``` and copy/paste back what it spits back. 

This will list what devices you have plugged in and will help us determine if its a cable problem or a software problem.


Let us know! :D

This is what I got:

Bus 001 Device 005: ID 03f0:4f11 Hewlett-Packard OfficeJet 5600 (USBHUB)
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Sorry it took me so long to get to this...had other issues with Natty- going on. Totally had no time for this. I would love to see what you think or maybe there isn't even a problem. Maybe I just need to know where to go and what to do to back up my stuff and see if it has been backed up.

Thanks for any help you can give.

---

### Post by sewbiz on 2011-06-12
Is there anyone that could help me with this?  I am assuming much to believe it is working the way it should.

---

