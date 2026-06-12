---
title: "How to install drivers for an old Adaptec CERC SATA RAID card in Ubuntu 10.10"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by abriejo on 2010-12-17
Hi

I am running Ubuntu 10.10 and trying to install the drivers for an Adaptec SATA RAID card.(Adaptec CERC)

I found this link : [http://manpages.ubuntu.com/manpages/hardy/man4/aac.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/aac.4.html)

I am think this is the driver I need.

There is a aac.4.gz that one can download, but I have no idea what to do with it and no idea how to : "compile this driver into the kernel"  because I do not know where the kernel configuration file is stored(This was a default installation - no special configurations.

May I ask you to please provide the steps to get these lines added to the kernel configuration file and any subsequent necessary steps?



Thanks!

AJ

---

### Post by cariboo on 2010-12-18
Have you actually plugged the device in and booted up the system? 

I needed some extra SATA ports so I bought a brand new inexpensive Adaptec Raid card from ebay ($12.00CDN including shipping), plugged it in booted the system, and the first thing I saw after power on was the raid setup options. I didn't have to install any drivers.

This is what lspci shows:

```
RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
```

The only problem I've run into so far after 3 weeks of uptime is the the card is Sata 1, so data transfer rates are a little slower than the onboard Sata 2 ports, which is really irrelevant as I use the server mainly for serving files to my media center pc running XBMC.

---

### Post by abriejo on 2010-12-20
Hi

Yes, I have plugged in the card an booted up.The card is immediately picked up , but the Ubuntu OS drivers for the card do not load.

---

