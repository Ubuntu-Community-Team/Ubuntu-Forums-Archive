---
title: "Move GRUB"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by bj218 on 2010-06-01
How do I move GRUB to WinXP MBR? Also how would I check on this move? I am 
currently running Ubuntu 9.10.

---

### Post by egalvan on 2010-06-01
> **bj218 said:**
> How do I move GRUB to WinXP MBR?

Exactly what do you mean by "move GRUB"? Is it already installed somewhere? Is it running OK?

And just for informative uses... :)

A Master Boot Record (MBR) does not "belong" to an operating system.

It "belongs" to a storage device which uses partition tables.

It usually contains boot code (Initial Program Loader (IPL) ) which may be system-specific (such as Windows Boot Loader), or one such as GRUB which is more system-agnostic.


I can guess you want to install GRUB on the MBR of the first hard drive, right?

---

### Post by bj218 on 2010-06-02
You are right I want to put grub on MBR!!

---

