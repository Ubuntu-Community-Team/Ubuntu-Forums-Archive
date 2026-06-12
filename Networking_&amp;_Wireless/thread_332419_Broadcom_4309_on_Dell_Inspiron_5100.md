---
title: "Broadcom 4309 on Dell Inspiron 5100"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by crag277 on 2007-01-06
I realize this is a very specific problem, but hopefully someone else has had the same problem before.  

I just installed Edgy on a Dell Inspiron 5100 that has a Broadcom 4309 rev 02 wireless card.  Needless to say I haven't gotten it to work yet.  I've been able to get the wireless to work fine on another laptop that has the broadcom 4318 using ndiswrapper, but the same method doesn't seem to be working on this computer.

I've tried using ndiswrapper 1.18 and 1.33 with a multitude of drivers.  Most of them let me see availible networks using network-manager-gnome, but I can never actually connect.

I've also tried using the bcm43xx-fwcutter method.  That wouldn't even let me see any wireless networks.

Hopefully one of you has the same computer and knows how to make this work!

Thanks for the help.

---

### Post by sridharvind on 2007-10-28
Duh, I seem to be having the same problem with Gutsy on an Inspiron 5100 with a BCM4309 rev 2 chipset. Been trying to get it to work this whole weekend. Any suggestions?

---

### Post by rkolb86 on 2007-11-30
just curious if anybody got this to work yet. I havn't had much success with 7.10. Recognizes there is a wireless card but doesn't see any networks or connect to any.

---

### Post by moose4204l on 2007-12-11
I am having the same problem . I have a dell inspiron 5100 and i have a bcm4309 card. I cant get it to work with Gutsy. I went to system > synaptic update manager > clicked on the  two ndiswrapper and the short n word right above them. ( sorry im on a windows computer right now )

nothing is working and I cant find anything in these forums that will help. I remember getting it to work in Fiesty Fawn with command line but it was like three or for short lines. when i search here I am getting pages of instructions and I never did anything like that before. 

Any Suggestions UBUNTU PEOPLE!!?!?

---

### Post by kevdog on 2007-12-11
Directly from the Broadcom website:

```
supported

    * bcm4303 (802.11b-only chips)
    * bcm4306
    * bcm4311 rev 1 / bcm4312
    * bcm4311 rev 2 / bcm4312 (needs patches for 2.6.24)
    * bcm4318 

unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * There is no support for any Draft 802.11n features.
    * BCM4328
```

Since 4309 is not supported, then you will have to use ndiswrapper -- Sorry!

---

