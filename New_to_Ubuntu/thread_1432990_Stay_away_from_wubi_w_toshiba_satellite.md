---
title: "Stay away from wubi w/ toshiba satellite"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-18
I couldn't get live disk to play nice last year and I've been seeing a few posts about wubi in here.  I just wanted to share my experience w/ wubi.   This was on my old lappy (toshiba satellite 32 bit)  Wubi constantly wanted to download as a 64 bit OS and when I relented thinking there may be an alternative in the installer (why else would canonical not release a 32??) (at least last may)  it messed up my MBR.  wubi is a dangerous beast.  I guess I should have known better though....

---

### Post by M!K3_$ on 2010-03-18
Could you give us more details on your satellite?

Just so people can use this for reference.

---

### Post by M!K3_$ on 2010-03-18
Have you tried installing wubi off of the 32-bit disk?

Burn a 32-bit Ubuntu disk, pop it while running windows and install wubi off the disk.

---

### Post by bradmayne04 on 2010-04-06
wubi off a disk?  I download it and it just started installing while i was in windows.  I'll have to get the satellite model for you all so you can be aware...  I never have time anymore... and when i do i'm sleeping my life has gotten really busy since coming home from prison....

---

### Post by candtalan on 2010-04-07
> **bradmayne04 said:**
> wubi off a disk?  I download it and it just started installing while i was in windows.

Wubi is included in the normal desktop Live CDs of Ubuntu. When Windows is running, just insert the Live CD and one option (the second one I think) offers to install Ubuntu inside Windows as a windows program.

---

### Post by egalvan on 2010-04-07
> **bradmayne04 said:**
> and I've been seeing a few posts about wubi in here.  I just wanted to share my experience w/ wubi.   This was on my old lappy (toshiba satellite 32 bit)**  it messed up my MBR**.  wubi is a dangerous beast.  I guess I should have known better though....

WUBI....
resides completely within Windows.
boots from within Windows.
runs completely within Windows.
and does not touch the MBR.

Many posts of folks not liking WUBI.

But it's not a dangerous beast.

---

### Post by lisati on 2010-04-07
Sorry to hear of the hassles.
No trouble with Wubi on my M200-series Toshiba Satellite laptop when I was using it. But then, mine has Vista, not Windows 7 - could this be a confounding factor?

---

### Post by 3rdalbum on 2010-04-07
> **bradmayne04 said:**
> Wubi constantly wanted to download as a 64 bit OS

If Wubi wanted to download a 64-bit edition of Ubuntu, then you've got a 64-bit CPU.

> it messed up my MBR.

Wubi doesn't touch your MBR. It adds a new entry to the Windows bootloader.

Wubi has crippling limitations and it's only really useful for a very small number of users, which is why I don't recommend it. Sooner or later your Windows will crash, and you'll lose BOTH operating systems. Or you'll outgrow the 30 gigabyte maximum space for Wubi.

---

### Post by ubun2warrior on 2010-04-07
i also used wubi, it just installs ubuntu in windows and ubuntu can be removed from uninstall programs from the control panel. I think its quiet harmless.

---

### Post by ubun2warrior on 2010-04-07
how can i create new threads or post queries ?

---

### Post by mechro on 2010-04-07
> **ubun2warrior said:**
> how can i create new threads or post queries ?

"New Thread" button on each forum's index page.

---

