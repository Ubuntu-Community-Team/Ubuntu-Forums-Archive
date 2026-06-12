---
title: "Upgrade from 12.04 to 14.04 problems"
date: 2014-08-18
forum: Networking &amp; Wireless
---

### Post by gorkygd67 on 2014-08-18
Hello people,

Yesterday I decided to do the upgrade. Little did I know, I got a black out, the upgrade was interrupted and the rest is history. Now I am facing the following issues:
1) No GUI when I open up the pc I am presented with the terminal, I log in every file seems in place but no GUI. Seems that Unity is not installed. I try to install it but then I bumb up to the second error
2) No internet connectivity (wired and wireless). When on `ifconfig -a` I only get `lo`. I downloaded the drivers, compiled them but still no luck. Really need your help on this.

Laptop Lenovo G550

Broadcom BCM4312
Realtek RTL8101E

---

### Post by user1397 on 2014-08-18
Do you have your files backup up?  I would honestly recommend a fresh reinstall of 14.04 if you have all your data backed up anyway, will most likely cause less headaches then attempting to fix a botched upgrade.

---

### Post by gorkygd67 on 2014-08-18
I have some of it. It's really a pain to backup everything and I do not mind losing some stuff (although I'd rather I didn't). How can I clean reinstall 14.04 without losing my stuff and replacing only the OS files?

---

### Post by user1397 on 2014-08-18
did you make a separate /home partition or is your entire install in one partition (aka just /) ?

---

### Post by gorkygd67 on 2014-08-18
I dont think I made a different partition. I used the default settings. It's probably just / .

---

### Post by user1397 on 2014-08-19
Then there isn't really an easy way to make sure all your files are backed up.  If you had separate / and /home partitions then you could reinstall the system to / and not touch the /home partition.  

You did say you are able to login with the command line and see your files that way.  In that case, you could backup anything you want just by sticking a flash drive/external hard drive and use terminal commands to copy files and folders to that drive.

---

### Post by westie457 on 2014-08-19
@ gorkygd67
From looking at your first post it looks like the download finished and the installation of the updates started.
Can you boot into 'recovery' mode from the Grub menu?
If so run through these options in this order:

FSCK #this will check for file system corruption. 

DPKG #this will configure from the cached downloaded files

If these do not work properly go to the next stage 
Enable Network #you will need an ethernet cable for this to work
Run DPKG again #this time any needed packages will be downloaded.

Let us know what happens.

---

### Post by Hadaka on 2014-08-19
Hi, as a last resort you can try to get a wireless connection by following
wild man's offline driver loading . post #8
[http://ubuntuforums.org/showthread.php?t=2117874](http://ubuntuforums.org/showthread.php?t=2117874)
good luck

---

