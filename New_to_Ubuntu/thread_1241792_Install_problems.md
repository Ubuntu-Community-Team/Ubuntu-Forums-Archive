---
title: "Install problems"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Corax1dom2Corvus on 2009-08-16
Ubuntu 9.04 64 bit. System dual core AMD, Nvidia GeForce 6800 GS, NEC Multisync 90GX2, raid disc system.

The 'plain' install CD gives the option to do a 'safe' graphics install, but does not set up the raid. On re-boot grub fails with 'boot failure', no system disc.

The 'alternative' install CD does not give a safe graphics install but does set up the raid correctly. On re-boot produces a vertically stripped screen with 'out of range' message. I can get into the 'rescue mode' boot. When there I've tried the various options that I've found in the forums. None of them have worked!

The RAID is a fake on the motherboard, Nvidia drivers.

Any further suggestions, as I would like to use Ubuntu.

---

### Post by nhasian on 2009-08-16
hello,

do you have SCSI hard disks and a dedicated Raid controller?  or are you just using the software based (fakeraid) from the motherboard?  please take a look at:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

