---
title: "How to install GRUB in boot partition in dual boot"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by Yash Pal on 2011-08-21
I want to install Ubuntu 11.04 alongside existing windows 7 (Dell inspiron laptop). 
 
The installation instructions for dual booting Ubuntu are quite good (there are many good sites). They generally recommend manual partitioning of the portion of hard disc where Ubuntu is to be installed and that a /boot partition is to be created along with other partitions.
 
They also recommend that the /boot partition be set up in the portion assigned to Ubuntu instead of in MBR as GRUB would be corrupted when installing updates for Windows. Subsequently, EasyBCD is to be installed in Windows and configured.
 
However, no one, absolutely no one, says or explains how GRUB is to be installed in /boot partition.
 
After searching the net, I think that GRUB will ask during installation about where it is to be installed. 
 
Could anyone enlighten me about how to install GRUB in the same partition and not overwrite MBR of Windows.

---

### Post by sanderd17 on 2011-08-21
Grub is always installed in /boot, and the MBR has to be overwritten.

In fact, the MBR loads GRUB from /boot on a certain partition.

If you don't overwrite the MBR, than GRUB can not be loaded.

---

### Post by raja.genupula on 2011-08-21
do you want to consider your ubuntu grub as main grub ?

---

### Post by sanderd17 on 2011-08-21
> **raja.genupula said:**
> do you want to consider your ubuntu grub as main grub ?

Since it is alongside Win7, I suppose it will be the only grub.

---

### Post by oldfred on 2011-08-21
I think you are mixing up grub2 and grub2's boot loader. Grub has a lot of software installed to various places but all MBR(msdos) computers can only boot from the MBR. So  you have to have a boot loader installed to the MBR to boot. 

Windows boot loader does not boot Ubuntu. Some have used EasyBCD, another boot loader with win7 to also boot Ubuntu.

I do not recommend not do you necessarily need a separate /boot partition unless you have an old computer or server with LVM or RAID and not always in those cases.

GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

I do not know nor use easyBCD as I like grub2 and only have XP which does not have a BCD.
[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

---

### Post by Yash Pal on 2011-08-22
> **raja.genupula said:**
> do you want to consider your ubuntu grub as main grub ?

I do not know. In earlier PC, I had XP and Ubuntu 7.04. I tried to download a programme from the net and Ubuntu would not boot. Eventually I reformatted the HD through XP and removed Ubuntu. Was Ubuntu's GRUB the main loader then? No idea.

[Grub is always installed in /boot, and the MBR has to be overwritten. In fact, the MBR loads GRUB from /boot on a certain partition. If you don't overwrite the MBR, than GRUB can not be loaded.]
As per this statement by 'sanderd17' the Windows MBR has to be overwritten.

'oldfred' clarified and directed me to sites which explain concept and sequence of boot loading.

I am extremely thankful for the help extended.

'However, no one, absolutely no one, says or explains how GRUB is to be installed in /boot partition.' - remains valid.

---

### Post by sanderd17 on 2011-08-22
> **Yash Pal said:**
> 

'However, no one, absolutely no one, says or explains how GRUB is to be installed in /boot partition.' - remains valid.

It is very hard on Ubuntu to install GRUB somewhere else than in /boot. If you follow the installation wizard, GRUB will be installed in /boot.

---

### Post by Yash Pal on 2011-08-22
> **sanderd17 said:**
> It is very hard on Ubuntu to install GRUB somewhere else than in /boot. If you follow the installation wizard, GRUB will be installed in /boot.
 
Thanks: I have messed up earlier and I wanted to be doubly sure. A non IT person like me would Install maybe once in 2-3 years and would have forgotten the sequence, precautions etc.

---

