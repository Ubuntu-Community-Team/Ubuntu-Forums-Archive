---
title: "how to manually boot"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by audit on 2011-04-23
I was experimenting with natty on a partitioned drive and now I am unable to boot to any other OS.

If I can get to the another OS I can reinstall grub-pc and will be able to work on my computer as I have always done. 

I know this because this is the second time I have had this problem. I am having multiple problems with Natty. (seems it does not play nice with one of my proprietary drivers.)

Last time I got around this by repartitioning my drive and installing Ubuntu 10.04. It is still their and there has to be a way to manually boot to 10.04 and reinstall grub-pc.

MY question: how do I manually boot to a particular OS on a partitioned drive?

---

### Post by audit on 2011-04-23
I have been able to work around my problem by installing startupmanger and changing the order of default OS. 

But I would still be interested in how you boot to a specified partitioned.

---

### Post by Elfy on 2011-04-23
I'd have reinstalled grub2 for the working OS 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by oldfred on 2011-04-23
If you get to the grub menu for Natty, but cannot boot the other entries for some reason you can either manually edit an entry  with e , or go to the command line with a c.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

A couple of ways:
Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

---

### Post by perspectoff on 2011-04-23
As always, I recommend setting up a boot partition with Grub Legacy in it, to chainload every other bootloader on your system (including Grub2).

Then you will not be in this pickle ever again.

Ubuntuguide:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

Kubuntuguide:

[http://www.kubuntuguide.info/index.php/Multiple_OS_Installation](http://www.kubuntuguide.info/index.php/Multiple_OS_Installation)

---

### Post by grahammechanical on 2011-04-23
Here is a link to the documentation on Grub2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Notice this line under the heading Hidden

> 
[LIST]
[*]No menu entries are displayed. The splash screen, if configured, will be displayed. 
[*]The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. 
[LIST]
[*]GRUB  2 searches for a depressed SHIFT key signal during boot. If the key is  pressed or GRUB 2 cannot determine the status of the key, the menu is  displayed. 
[/LIST]
[/LIST]


I am also testing 11.04 Beta on a separate partition. Grub2 has been updated about three or four times in the last three weeks. The last time was a few days ago. The update always installs the 11.04 version of Grub2 in the MBR and it overwrites my standard 10.10 Grub2. The boot order is changed and the Grub splash background image disappears but (and this is the important part) I always get a menu that lists all the OS that I have on the drive.

So, I ask, why are you not getting that menu? Answer: Don't ask me! I do not know. Perhaps the timeout is so short that Grub does not have time to display a menu before it begins to load the OS.

I do get a menu. So, I can select 10.10 and use Grub Customizer (search for grub-customizer in synaptic or the software centre). I use the install to MBR option to put the 10.10 Grub2 back into the MBR. and I get the boot menu back to the way I like it. It seems that having our preferred Grub2 overwritten a few times is the price we pay for testing a Beta version.

Regards.

---

