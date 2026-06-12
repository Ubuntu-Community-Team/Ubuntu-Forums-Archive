---
title: "Hardware / Installation problems"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Stalker72 on 2009-01-24
My motherboard is an Asus P6T Deluxe with an integrated Marvell SATA controller card. After asking for help on Ubuntu's IRC channel, I found out that it doesn't support Linux. I recently bought a new card from Adaptec. It hasn't arrived yet.

I've tried to install Kubuntu several times, with the normal CD, the minimal installation CD and the alternative CD, to no avail. I've also tried the Linux Mint CD. I know that the problem is related to my hardware, but not just the SATA controller card.

I think there's a problem with something else than the SATA controller card too. Even the XP installation failed. Both times I ended up with a BSOD.

None of the Marvell adapters detect it, but my BIOS does.

Thanks,

Stalker72

---

### Post by yeats on 2009-01-24
Are you able to boot into the live CD?

---

### Post by Stalker72 on 2009-01-24
No. When I try to boot into the live session or install, I just get a black screen with text saying something with BusyBox and (initramfs).

Stalker72

---

### Post by Stalker72 on 2009-01-24
Do I need to disable something in BIOS?

Stalker72

---

### Post by yeats on 2009-01-24
Hmm.  What are your current specs?  Memory, disk, processor, etc.?  Also, did you verify the ISOs with md5sums and do a CD integrity check on each CD you've made?  Trying to install with a corrupt disk is major trouble.  Also, do you know for certain that your CD-ROM drive is working properly?  I had a CD drive fail completely mid-install :-) with this result (BusyBox - which is mostly useless unless you're already an expert with the command line).  Check all these things and post back . . .

---

### Post by Stalker72 on 2009-01-24
Asus P6T Deluxe
Sony NEC Optiarc AD-7220S-0B
Western Digital Caviar Black 1 TB
Intel Core i7 920
OCZ DDR3 PC3-10666 Intel i7 Triple Channel 3 GB
Point Of View GeForce GTX 260
Chieftec Turbo Series 850W

I did verify it with md5sum and I ran the integrity check.

I'm pretty sure the optical drive works fine.

Stalker72

---

### Post by diablo75 on 2009-01-24
You might try using the Alternate CD to see if Ubuntu will install.

---

### Post by yeats on 2009-01-24
I agree with diablo - this is how I ended up needing to install during the CD-ROM failure debacle I described above :-)

---

### Post by Stalker72 on 2009-01-25
**Update:**

Now my PC doesn't even want to read CDs or memory sticks.

I took some pictures of my BIOS so it's easier to solve the problem:

[http://bayimg.com/kaNOdaAbC](http://bayimg.com/kaNOdaAbC)
[http://bayimg.com/kaNoEAAbC](http://bayimg.com/kaNoEAAbC)
[http://bayimg.com/kaNofaAbc](http://bayimg.com/kaNofaAbc)
[http://bayimg.com/kANoGAAbc](http://bayimg.com/kANoGAAbc)
[http://bayimg.com/kAnOHAABC](http://bayimg.com/kAnOHAABC)
[http://bayimg.com/KaNoIaaBc](http://bayimg.com/KaNoIaaBc)
[http://bayimg.com/kaNoJAABC](http://bayimg.com/kaNoJAABC)

If you need pictures of other parts of the BIOS or just more information, don't be afraid to tell me!

Cheers,

Stalker72

---

### Post by Stalker72 on 2009-01-25
When I first created this thread, I had connected the HDD and optical drive to the SAS ports instead of the SATA ports.

The SATA ports uses an integrated Intel controller, so none of the Marvell controllers detect anything now, logically.

Stalker72

---

### Post by Stalker72 on 2009-01-25
When the PC gets to the point where it's supposed to read CDs and removable devices, it just reboots automatically, and it keeps rebooting like in a loop.

Stalker72

---

### Post by Stalker72 on 2009-01-25
Bump!

Stalker72

---

### Post by Stalker72 on 2009-01-25
My PC still can't read CDs, but now it can read memory sticks. I managed to install Ubuntu with one, but when I boot up I get thrown to a command line. What should I do?

Stalker72

---

