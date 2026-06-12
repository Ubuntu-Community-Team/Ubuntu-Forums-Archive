---
title: "Just a note about last update - if you lose Internet access..."
date: 2010-05-07
forum: New to Ubuntu
---

### Post by texla on 2010-05-07
Hey - just a note to those newbies like me who may have this issue because I "lost" my internet access after the updates from yesterday.  In case you do, just go to users and groups in the system administration area and click on advanced settings.  Enter password.  Then go to user privileges.  The item "connect to internet using a modem" was unchecked for me.  I checked it then rebooted and all is fine now!  Whew - it was abit hard to figure out wat first but it was simple as can be.... peace

---

### Post by _0R10N on 2010-05-07
Wow!! that's weird!! did some error occur when upgrading? I'm asking this because those configurations don't use to change on updating/upgrading. I'm also thinking in some compatibility with network hardware issue. Please, post the output of
```
lshw -C network
```

Kind regards!

---

### Post by texla on 2010-05-07
> **_0R10N said:**
> Wow!! that's weird!! did some error occur when upgrading? I'm asking this because those configurations don't use to change on updating/upgrading. I'm also thinking in some compatibility with network hardware issue. Please, post the output of
```
lshw -C network
```Kind regards!
I know - this was a strange one for me, too.  As fas as I remember, it did happen as I said it - I did the update, let it restart and then, boom - nada on the internet.  Here's the output you asked for:
(I have already turned the internet back on if that helps)

  description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:e3:21:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.2 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:e400(size=256) memory:cffff400-cffff4ff

---

