---
title: "How do I boot Ubuntu on a partition in another harddrive?"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by A_Squirrel on 2011-04-01
It's been a few years since I've used linux or Ubuntu, and my knowledge has dried up considerably. Even so, I'd never done anything much more than a default sort of installation and set up apache.

Now I'm faced with installing ubuntu on a partition of a harddrive that is not the default harddrive. Even worse, the system uses Vista Home Premium. 

I installed Ubuntu on the partition, but now I have no way of reaching it. (Oh, I manually partitioned it.) All the folders are sitting there on an ext4 filesystem, but I have no way to boot into it. No option appears in the BIOS when I fire up the PC. I've been searching around the internet but the only thing I've come across is GRUB, but I don't know if it's relevant or how to use it.

From my memory:
(Windows is installed on hda, ubuntu on a partition of hdd).
(The version of Ubuntu is 10.0.0.4)

Please help! Ubuntu is just sitting there taunting me!

*Edit -- I also tried using the GParted utility to flag the filesystem with the boot flag, but to no avail.

---

### Post by andrewthomas on 2011-04-01
You are either going to have to install Grub2 to the MBR of sda, or change the boot order in BIOS to boot sdd first (If you did, in fact, install grub2 to the MBR of sdd.)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by grahammechanical on 2011-04-01
GRUB is a boot loader that searches the hard drives for operating systems and then creates a menu to let you select the OS you wish to load. It will then load the OS of your choice.

How did you install Ubuntu? Was it from a live CD? Do you have any data on the Ubuntu partition that you do not want to lose? Most probably not, as you say you cannot access Ubuntu. I was just checking.

You can reinstall Ubuntu and this time when it asks if you want to install Grub in the MBR of the first hard disc partition then say, Yes. The next time you boot Grub it should load and give you a menu.

Regards.

---

### Post by oldfred on 2011-04-01
You may just have to reinstall grub.

Post this so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by ferd on 2011-04-04
-

---

