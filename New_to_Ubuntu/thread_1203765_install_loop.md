---
title: "install loop"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by iScorpious on 2009-07-03
greetings. irecently did a wubi install on my pc-liked it. So i decided to set it up on its own- seperate from my vistaHP; ive already set up a clean-reformatted(NTFS)partition just for this (uninstalled the orig. sbys)& re-dl'd the distro(9.04) direct to the new partition but when i try to install from the wubi icon in the file i get:  the installer/click on the only option=install sidebyside/click reboot now--IT JUST RETURNS TO THE INSTALLER WINDOW

so pls, lets START w/that
Ray

---

### Post by earthpigg on 2009-07-03
i think you are confused about a few things :P

putting the .iso on a random ntfs partition wont really do anything...

the way to do a clean ubuntu install:

1) download the iso
2) burn it as an image to a cd
3) set up your computer to boot from cd (may not be needed) in the bios
4) insert cd
5) reboot
6) follow onscreen instructions

hope that helps

---

### Post by iScorpious on 2009-07-05
EP- thx. i do feel like a fool=20 min after posting i realized the live disc WASNT in my cd drive ,DUH! of course as soon as i inserted it all worked fine. BUT- i didnt realize that the installer had a gpart (because i'd only done the side byside before) --so i set up the new partition seperately before hand= now i HAVE the dual boot & both (UBU & Vista) are working just great EXCEPT= now i hav an Ubuntu program folder in the vista boot partition(no idea how it got THERE, do u think i can delete this w/o undoing my dual boot?) AND the new partition the installer set up AND a dead partition from my original ineptness that i & cant seem to reintegrate into ANY of the partitions (thankfully i only made it  5Gb)- so ive temp. unallocated it & set it aside to deal w/later. thx again, Ray

---

### Post by LewRockwell on 2009-07-05
[http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/](http://www.linuxhaxor.net/2008/12/06/graduate-from-a-wubi-install-to-a-dedicated-partition/)

.

---

### Post by earthpigg on 2009-07-05
> **iScorpious said:**
> EXCEPT= now i hav an Ubuntu program folder in the vista boot partition(no idea how it got THERE, do u think i can delete this w/o undoing my dual boot?) AND the new partition the installer set up AND a dead partition from my original ineptness that i & cant seem to reintegrate into ANY of the partitions (thankfully i only made it  5Gb)- so ive temp. unallocated it & set it aside to deal w/later. thx again, Ray

as far as the folder in windows -- assuming you set everything up as you describe, you should be able to toss it without it doing any harm. instead of removing it, just rename it something else to test :P you have uninstalled 'ubuntu' in windows add/remove programs, right? it is only talking about the wubi install of ubuntu, not the install you just did.

if you want to take a look at your partitions, boot from the live cd again, 'try without making changes to computer', and once you get to the live cd desktop:

applications->accessories->terminal -> and type gparted


note that gparted can not do anything to drives that are 'mounted', hence the need to boot from the cd.

---

### Post by iScorpious on 2009-07-06
EP & Lew -

thx guys; i'll spend some time today with ur suggestions; let u kno later
REALLY appreciate ur feedback
R:p

---

### Post by iScorpious on 2009-07-08
EP- was successfull in uninstall from winPartition w/ no impact on anything
(except a desireable 10Gb increase in free disk space - any thots on why so large, not that its really important- just seemed big)= ive burned a Gparted disk but thx for the info that its also still accessible from the Ubudisk=ur help was invaluable, much appreciated

LEW- reviewed info at the link= wuduv been the ideal but a bit late, damage already done BUT also a big thx

**NEXT,** please:

when my boot screen comes up it shows (2)versions of Ubu ea. w/recovery
v9.04 kernel 2.6.28-11 & -13 (as well as the memtest & my VistaMain &Recovery)

_**are both kernel v. necessary?**_ ive been loath to try the 2nd one(cant recall @moment which is listed 1st)= if not, what are ur thots?
Ray

---

