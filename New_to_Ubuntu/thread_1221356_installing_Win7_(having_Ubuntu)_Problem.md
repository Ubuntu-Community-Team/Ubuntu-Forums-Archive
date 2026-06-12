---
title: "installing Win7 (having Ubuntu) Problem"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Dr.iCe on 2009-07-23
i get an error about it not having several partitions and that its not NTFS or something.. i am going to try GParted now but i would love some help..  i am not "leaving" ubuntu, but i am going to have a dual-os ;D because i need programs for my working which wont work in Wine and stuff..

---

### Post by Rocket2DMn on 2009-07-23
Does it not let the Windows install because there are non-NTFS partitions?  It really shouldn't be a showstopper.  As long as you are not trying to install to those partitions, it should let you proceed.

If you haven't allocated space for Win7 yet, then yes, you need to run GParted from a LiveCD and resize your existing partitions to make room for Win7.  You can get the GParted LiveCD here - [http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

As always, back up your data before fiddling with partitions and installing other operating systems!

---

### Post by Dr.iCe on 2009-07-23
> **Rocket2DMn said:**
> Does it not let the Windows install because there are non-NTFS partitions?  It really shouldn't be a showstopper.  As long as you are not trying to install to those partitions, it should let you proceed.

If you haven't allocated space for Win7 yet, then yes, you need to run GParted from a LiveCD and resize your existing partitions to make room for Win7.  You can get the GParted LiveCD here - [http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)

As always, back up your data before fiddling with partitions and installing other operating systems!

seems like you've fully understood my problem..
**but i really need a fully detailed guide about how to do this**
ive gotten GParted thru the  Add/Remove Applications thing but i dont know if thats what i should use or anything.. do i need to burn the disc??
please give me a VERY detailed guide to help me out..

---

### Post by Rocket2DMn on 2009-07-23
You can't resize your Ubuntu partition(s) from within Ubuntu, which is why it needs to be done from a LiveCD.  The easiest thing to do is to use the GParted LiveCD.  Alternatively you can use an Ubuntu LiveCD and run GParted from there (System->Administration->Partition Editor).  If you do use the Ubuntu LiveCD instead of GParted, make sure you right click on the Swap partiiton and click unmount, or open a terminal and run
```
sudo swapoff -a
```
That is because it automounts swap space.

For a detailed guide on changing partitions, have a look at [uhelp]community/HowtoPartition[/uhelp], and particular see [uhelp]community/HowtoPartition/ResizingPartition[/uhelp].  Since you are new, I recommend taking your time and reading through that stuff, it will explain a lot.

If you have any specific questions, please feel free to ask here.  Effectively what you are going to need to do is to resize (shrink) your root partition (probably formatted as ext3 or ext4) to make empty space.  In that empty space you will create a NTFS partition that you will install Win7 to.  Just be sure you make it large enough for Windows.

---

### Post by Dr.iCe on 2009-07-23
> **Rocket2DMn said:**
> You can't resize your Ubuntu partition(s) from within Ubuntu, which is why it needs to be done from a LiveCD.  The easiest thing to do is to use the GParted LiveCD.  Alternatively you can use an Ubuntu LiveCD and run GParted from there (System->Administration->Partition Editor).  If you do use the Ubuntu LiveCD instead of GParted, make sure you right click on the Swap partiiton and click unmount, or open a terminal and run
```
sudo swapoff -a
```That is because it automounts swap space.

For a detailed guide on changing partitions, have a look at [uhelp]community/HowtoPartition[/uhelp], and particular see [uhelp]community/HowtoPartition/ResizingPartition[/uhelp].  Since you are new, I recommend taking your time and reading through that stuff, it will explain a lot.

If you have any specific questions, please feel free to ask here.  Effectively what you are going to need to do is to resize (shrink) your root partition (probably formatted as ext3 or ext4) to make empty space.  In that empty space you will create a NTFS partition that you will install Win7 to.  Just be sure you make it large enough for Windows.
well i dont have the Ubuntu disc atm. so i will need to burn out the GParted am i right?
after burning it i will reboot?
do i need to press anything while booting??

i just want it as detailed as possible so i dont screw up

---

### Post by rbc on 2009-07-23
All you to do is make BIOS is set to boot from the CD drive, before that hard drive. No you don't need to press anything. Be prepared, though, the Windows bootloader is going to overwrite grub, so you are going to have some repairs to make after Windows is installed

Edit: This is the repair you will doing, in case you want to ask questions now, or read up. Not really that difficult
[http://ubuntuforums.org/showthread.php?t=1221381](http://ubuntuforums.org/showthread.php?t=1221381)

---

### Post by Rocket2DMn on 2009-07-23
> **Dr.iCe said:**
> well i dont have the Ubuntu disc atm. so i will need to burn out the GParted am i right?
after burning it i will reboot?
do i need to press anything while booting??

i just want it as detailed as possible so i dont screw up

Yes, burn the GParted .iso image to a cd-r as an image (not as data!).  You can use Brasero for this - Applications->Sound & Video->Brasero Disc Burner.  Keep the disc in the cd tray and reboot.

You can set your BIOS to boot from the CD first as the previous poster said, but usually you have the option to enter a Boot Menu right when the computer reboots so you shouldn't have to enter the BIOS if you don't want to.  The Boot Menu option is usually easier since you don't have to go undo your changes to the BIOS afterward.  To do either of these, you have to press F12 or some other key at the beginning of the boot sequence, you may only have a second or so to do it.  It should say on the screen, perhaps near the upper right corner which button(s) to press to enter Setup (BIOS) or the Boot Menu.  Since it usually only appears for a second or two at most, you may need to try a couple of times before you read it and have time to press the correct key :)

It will boot into the GParted LiveCD and should have GParted already running for you - if not it should be pretty easy to get to.  From there you can follow the directions I linked you to earlier.

---

