---
title: "Have a Dell Inspiron 1150 and can't connect to wireless"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by smfwallengren on 2008-06-02
I have a dell inspiron 1150 and just installed ubuntu.  Im running the 8.04 release kernel linux 2.6.24-17 with a BCM4309 802.11a/b/g (rev 03) wireless card.  I have tried different ways, but cant seem to get it to work.  Now when I try to enable the driver my computer freezes.  Please anyone, help me.

---

### Post by Ayuthia on 2008-06-03
> **smfwallengren said:**
> I have a dell inspiron 1150 and just installed ubuntu.  Im running the 8.04 release kernel linux 2.6.24-17 with a BCM4309 802.11a/b/g (rev 03) wireless card.  I have tried different ways, but cant seem to get it to work.  Now when I try to enable the driver my computer freezes.  Please anyone, help me.
Can you tell us which way you tries to get your wireless to work?  I am guessing that you are trying to use ndiswrapper since your computer froze.  If this is the case can you post the make and model of your computer along with the following (from the Terminal):
```
ndiswrapper -v
ndiswrapper -l
```

---

### Post by vexingmodstwo on 2008-06-03
I highly recommend [Jamie Jackson's How To]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") for Broadcom cards.  If that doesn't work it will get you 99% there and I finally got connected when I switched to wifiradar.

---

