---
title: "Disable PNP OS in Bios?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Prizm1 on 2009-03-26
I read somewhere at a Linux beginners webpage that users should disable PNP OS in the BIOS. Is this correct for Ubuntu Linux users? Does Ubuntu update the ESCD in Bios (PNP OS)?

---

### Post by spcwingo on 2009-03-26
No problems here with any of my systems (I have approx 9 machines one flavor of Linux or another).  I'm almost certain that none of my CMOS settings have been changed by Ubuntu on any machine...I just checked my latest build and nothing is touched in BIOS setup.

---

### Post by Prizm1 on 2009-03-28
> **spcwingo said:**
> No problems here with any of my systems (I have approx 9 machines one flavor of Linux or another).  I'm almost certain that none of my CMOS settings have been changed by Ubuntu on any machine...I just checked my latest build and nothing is touched in BIOS setup.
Well, I suppose that I am just trying to determine whether or not PNP OS BIOS setting should be disabled for Ubuntu or Linux in general. Some posts seem to suggest that this setting in the BIOS should be disabled for Linux.

---

### Post by CatKiller on 2009-03-28
While the PNP OS BIOS specification was originally designed by Microsoft to allow Windows 95 and 98 to work, even the more recent versions of Windows ignore it. It basically specifies whether the BIOS should attempt to resolve IRQ and DMA conflicts, or let the OS do it. Since most OSes basically ignore the results of this setting, you might as well turn it off. Similarly, since most OSes basically ignore the results of this setting, it really doesn't matter if you do. I've never had any problems, or significant differences in behaviour, no matter which way this option was set. It's a legacy thing that makes no real difference.

---

### Post by Pbethe on 2010-09-06
> **Prizm1 said:**
> Well, I suppose that I am just trying to determine whether or not PNP OS BIOS setting should be disabled for Ubuntu or Linux in general. Some posts seem to suggest that this setting in the BIOS should be disabled for Linux.

IIRC, it makes a difference to SUSE.  I don't know about Ubuntu.

---

