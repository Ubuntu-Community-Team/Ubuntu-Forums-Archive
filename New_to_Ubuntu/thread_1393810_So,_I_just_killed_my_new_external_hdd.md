---
title: "So, I just killed my new external hdd"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Nedrah on 2010-01-29
Hey everyone,

I just tried installing Ubuntu on my brand new external hdd.
That went terribly wrong, since grub could load neither windows nor ubuntu anymore. 

Well, I was able to at least restore my win7 boot by using a rescue disk. 

HOWEVER, my external hdd is not recognized by windows anymore. It treats it as an unknown usb device. 

I really (really!) need some help here.

---

### Post by milton1 on 2010-01-29
probably the external drive has been wiped or formatted to something windows will not read by default (ext4, for example). Try reformatting the drive.

---

### Post by kansasnoob on 2010-01-29
Windows can't read ext3 and ext4 file systems.

---

### Post by Nedrah on 2010-01-29
Hey guys, thanks for your replies.

After creating this thread, I created a gparted boot cd. I booted from that cd. It also didn't recognize the hdd. 

To clarify:

I have a 1TB external hdd. I have ~900gb of that formatted as ntfs. I then ran ubuntu setup and created 2 partitions out of the remaining 100gb. 96 were reserved for "/" and 4gb for swap. 

I then installed ubuntu on the / partition. 
After that, I couldn't boot my pc anymore. grub just sat there, doing nothing. I then used a win7 recovery cd to restore my mrb. Afterwards, win7 would boot again. However, the external hdd I installed Ubuntu on is not recognized anymore. Not by Win7, not by Ubuntu, not by gparted livecd.

I think something's seriously wrong!

---

### Post by egalvan on 2010-01-29
OK, you state that it's  "BRAND NEW DRIVE"...
so it should have nothing of value that you want to save (back up)

IF THIS IS SO...

I do not use Windows 7, but XP had a Drive Management Console that allowed one to manage drives at the physical level.

next...
gparted should have a "drop-down" menu up in the right hand corner,
this is where you choose which PHYSICAL drive you want gparted to use.

see the attached screen-shot.

if this does not work, then it is possible that there are hardware problems.

---

### Post by Nedrah on 2010-01-29
Thank you, egavlan.

Gparted didn't see the drive.
Fortunately, there was a rather simple solution to the problem:

I unplugged the drive from its power supply. 
After doing that, I all of a sudden got full access to the drive again. 

Thanks for your help!

Anyways, I asked for advise on installing Ubuntu on an exernal hdd before. People told me to just set up the propper partitions and go ahead.
That went seriously wrong.

---

### Post by wilee-nilee on 2010-01-29
When you install on a external drive with a live cd you want to make sure to hit the advanced button on the final install screen and check where grub is going.

---

