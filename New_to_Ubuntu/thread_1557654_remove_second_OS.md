---
title: "remove second OS"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by L2U2K2E on 2010-08-21
okay, let me start this off by saying that I'm experimental and an idiot. I have my notebook set up with Ubuntu 10.04 as the main operating system, and I had a bunch of un-used HDD space, so I decided to play around with other Linux distributions.

First mistake: I installed lubuntu from the live CD in the empty space. after a few boots I was confident this was not for me.

Second Mistake: I booted me Gparted live CD and just deleted the partitions for lubuntu.

Unfortunately I didn't stop to consider that lubuntu was the first thing grub would attempt to boot. I ran into some crazy problems trying to figure out how to use GRUB, and eventually gave in and just reinsalled lubuntu.

Now, at least my system will let me get to the grub menu so I can boot my ubuntu partition, but there are plenty of problems. First, I still have lubuntu on my system and want it gone. Second, lubuntu partitions are listed above ubuntu on the grub boot and I have no idea how to change this.


someone help? and is there something I should do differently in the future if I would like to try dual booting with other OS's?

---

### Post by Rubi1200 on 2010-08-21
You can use the Ubuntu CD and boot the computer, choosing to try not install.

Use GParted on the LiveCD to delete any partitions you don't want.

Then, follow this guide to reinstall GRUB:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

This should then sort everything out and you will be left just with Ubuntu in the menu and on the drive.

You can also use this guide in the future if you decide to play around.

---

### Post by Gone fishing on 2010-08-21
I think I would

sudo apt-get install gparted 

This  will install gparted run gparted and remove the lubuntu partition.

Then 

sudo update-grub

Will rebuild the grub configuration without lubuntu you could also install Startup-manager 

sudo apt-get install update-manager

---

### Post by L2U2K2E on 2010-08-21
> **Rubi1200 said:**
> You can use the Ubuntu CD and boot the computer, choosing to try not install.

Use GParted on the LiveCD to delete any partitions you don't want.

Then, follow this guide to reinstall GRUB:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

This should then sort everything out and you will be left just with Ubuntu in the menu and on the drive.

You can also use this guide in the future if you decide to play around.

The final method on this guide actually fixed the problem. Thank you!

---

### Post by Rubi1200 on 2010-08-21
You are more than welcome!

:D

---

