---
title: "Un-installing Ubuntu"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by CyberPsyche on 2009-08-27
How does this work? i can't seem to do it and its impeding my efforts to install windows xp on my other pc. i'm really not very computer savvy(the main reason im un-installing linux), and i need some direction on how to do this. if someone cares enough to lend me a virtual helping hand it would be greatly appreciated, thanks:)

---

### Post by sahabcse on 2009-08-27
try to boot from winodows cd and remove and format the linux partition

---

### Post by zeroseven0183 on 2009-08-27
> **CyberPsyche said:**
> i'm really not very computer savvy(the main reason im un-installing linux)

You really don't need to be computer savvy to learn Linux/Ubuntu. :)

You just need to reformat your hard drive and install Windows, that's all.

---

### Post by CyberPsyche on 2009-08-27
thanks for the advice. well i already tried that multiple times and it doesn't seem to work. it just goes automatically to ubuntu os when i turn on pc even with the xp cd in the drive. i really  don't know why it doesn't go to the xp installation screen. this is very frusterating.

---

### Post by SunnyRabbiera on 2009-08-27
well what ubuntu problems were you having?

---

### Post by zeroseven0183 on 2009-08-27
> **CyberPsyche said:**
> thanks for the advice. well i already tried that multiple times and it doesn't seem to work. it just goes automatically to ubuntu os when i turn on pc even with the xp cd in the drive. i really  don't know why it doesn't go to the xp installation screen. this is very frusterating.

You should have a bootable Windows CD and your CD drive should be set as first boot priority. I hope you get the point.

---

### Post by automaton26 on 2009-08-27
This is going to sound difficult if you're not computer-savvy, but it might be that the hard drive is higher in the BIOS boot order than the optical drive. The BIOS holds some of the configuration information for your hardware.

You can enter your machine BIOS by pressing the correct key immediately after turning the machine on (check your manual, but it's often either the F2 or Del key). Then navigate the menus to move the optical drive to be higher priority than the hard drive, and then save the changes.

After that, when you reboot it will always look at the optical drive first.

---

### Post by davbren on 2009-08-27
> **CyberPsyche said:**
> thanks for the advice. well i already tried that multiple times and it doesn't seem to work. it just goes automatically to ubuntu os when i turn on pc even with the xp cd in the drive. i really  don't know why it doesn't go to the xp installation screen. this is very frusterating.

You need to select your boot device. To do this you'll need to go into the BIOS this will be something like 'Del' or 'F12' on Boot. If its a Dell, I think its F2 when the Boot starts. Then you have to pick. the drive with the windows cd in. :D

---

### Post by astrakhan on 2009-08-27
check the boot sequence in your bios settings and make sure your CD drive is first on the list. if it is usb drive then the usb devices must  be first in list

---

### Post by theozzlives on 2009-08-27
If Windows isn't recognizing the drive, then use the Ubuntu Live CD. Go to System > Administration > then (depending on the version) either GParted or Partition editor. Unmount and delete all partitions and go to Device > Create Partition Table.

However, I would urge you to reconsider totally getting rid of Ubuntu (I have nothing to gain either way). You could do Dual Boot, or even install Ubuntu under Windows (WUBI). But that choice is yours to make.

P.S. If you're not computer savy, you'll have a problem with cleaning all the malware that plagues Windows.

---

### Post by Keen101 on 2009-08-27
1. Check BIOS to boot CD. (usually by repeatedly pressing F2 before ubuntu boots)

2. Make sure you have a bootable XP CD. If you dont, then you face a chicken vs. egg scenario where a version of windows needs to be installed before you install XP.

3. if you are still having trouble find someone nearby who knows computers inside and out. (If worse comes to worse, you can create and use a GPARTED LIVE-CD to erase the ubuntu partitions. Then Ubuntu wont boot at all. You will just get a GRUB error.)

---

