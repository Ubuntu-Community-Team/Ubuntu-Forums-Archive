---
title: "Quad boot, Order of installation?"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Swerve1000 on 2009-03-30
Hi,

I need to install the following operating systems and am wondering in which order I should install them:

Ubuntu 8.10
XP
Vista
Windows 7

I want to use GRUB to select the OS when the machine boots (single hard drive machine).

I am thinking
> 
1st) XP
2nd) Vista
3rd) Windows 7
4th) Ubuntu 8.10

Would this work? Or should I install them in a different order?

Everything will be a fresh install.

Thank you!!

---

### Post by desperado665 on 2009-03-30
The best you can do in a single physical drive is tri-boot. Unless you have a secondary drive that you intend to use, quad-booting would not work as a hard drive is limited to 4 primary partitions.

---

### Post by Swerve1000 on 2009-03-30
Oh really, I didn't know that.

Thanks very much :)

---

### Post by JohnLM_the_Ghost on 2009-03-30
Anyway best practice is to Install all Windows'es, and then Ubuntu. Ubuntu can take care of existing installations, while Windows cares only for other Windows'.

Though I doubt you will be presented Quad-boot menu on GRUB. It is more likely GRUB will chainload to NT Windows chooser.

So it will go like this
GRUB:
- Ubuntu
- Windows loader

When you choose Windows loader it will present what windows'es you have.
But I doubt it will be a problem.

---

### Post by SuperSonic4 on 2009-03-30
> **desperado665 said:**
> The best you can do in a single physical drive is tri-boot. Unless you have a secondary drive that you intend to use, quad-booting would not work as a hard drive is limited to 4 primary partitions.

Ubuntu can boot from a logical partition so quad-booting would work

---

### Post by Swerve1000 on 2009-03-30
Thats great.

I'm going to install these 3 in the following order;

XP
Vista
Ubuntu 8.10

I'm tempted to install 9.04 beta, but would that update to the 9.04 official release? or would I have to do a fresh installtion?

---

### Post by kansasnoob on 2009-03-30
> **SuperSonic4 said:**
> Ubuntu can boot from a logical partition so quad-booting would work

I was thinking the same thing. Assuming that each Windows install uses only one primary partition that still leaves room for one extended partition and I've personally had as many as 4 different Linux distros sharing one extended partition.

I know nothing about Win 7 though!

9.04 Beta is relatively stable, but you can almost expect some "breakage" at this point in development. No big deal as long as you can boot into another OS for a day or two until the devs get things straightened out.

---

### Post by ranch hand on 2009-03-30
All 4 should be no problem.

Create 3 primary partitions and make the 4th extended.

Install the MS stuff on the 3 primaries.

Point the 8.10 CD at the Extended partition and it will make the installation partition and the swap partition right there or you could make the swap partition in the extended partition your self.

---

