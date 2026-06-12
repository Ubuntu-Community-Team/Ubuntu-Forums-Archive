---
title: "live cd does not autmatically start, vista overrides"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by reikidude on 2009-03-05
Hi,

My son in the Netherlands (Im in London) tries to install ubuntu on a HP Compaq 6720S but the live CD does not run immediately it look as if Vista overrules the Live CD I would have tried it if I was there. Does any one know what he should do. He does not speak sufficient English to ask it himself, so I'm doing it the long way round.

Many thanks,

Martijn

---

### Post by kanikilu on 2009-03-05
You can either change the boot order in the BIOS setup, or if you don't want to make any permanent changes to the configuration, most computers have a "temporary boot device" menu you can get to by pressing a key immediately after turning it on. Usually it will tell you what this key is, but it varies by manufacturer. On my Dell it's F12, but I've seen ESC (or was it Delete?, I can't remember...) on another computer.

---

### Post by Therion on 2009-03-05
Make sure the LiveCD was burned as a bootable .iso and NOT a data CD/DVD.  If you put the disk in the drive and then look at what's on it you're going to see one of two things:

1.  Only one file, ending in .iso - this means the disk was NOT burned as a bootable .iso and would explain the problem.

2.  Lots of files and a few folders on the disk.  This indicates the CD was burned correctly.  This would indicate that the optical drive is not in the boot sequence.  You'd need to enter the BIOS to adjust that.

I'm betting the problem is related to Possibility #1 however...

---

