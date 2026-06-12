---
title: "Ubuntu 9.10 wont boot"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by wize_gurl on 2011-05-19
Hi Everyone!
 
I have a Lenovo machine with Windows XP installed on it. I also installed Ubuntu 9.10 on the other drive. 2-3 days back, I tried to start my computer in Windows. The screen showed the Windows logo, and then suddenly the computer restarted. I tried a couple of times again, but the same thing happened. I tried to start in the Safe mode, still the same problem. It showed me different startup options, I chose the safe mode, it loaded up the drivers and then the computer restarted.
 
Since I had Ubuntu installed on the other drive, I tried working on that. I used the computer 2-3 times with ubuntu, downloaded the AVG Antivirus on it, to try to cleanup the other drive. For some reason, i couldnt see it on the system, so I restarted the computer. This time, the same thing happened to ubuntu. It showed the ubuntu sign, it took a really long time, and then a different log-in screen came up, and it said Gnome at the bottom. I tried logging on, but it would show a blank screen afterwards.
 
I would really appreciate help on this one, as i cannot work on my computer anymore, and I dont want to format it again. Is there a way I can repair it ???
 
I tried using the Live CD, and i can access my windows data atleast. I am trying to back it up. But it would be very helpful, if i can fix the problem without having to format my harddrive.
 
I am trying different approaches, and if anything works out, I will post the solution.
 
Thanks for your time.

---

### Post by sanderd17 on 2011-05-19
Repairing this will not be easy, but did you install ubuntu with wubi or on a separate partition? this makes a lot of difference.

I don't think there is anything wrong with your booting settings, but to be sure, could you run the boot info script from a live CD?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Maybe to solve the login problem in gnome:

go to a terminal (press CTRL+ALT+F1 at the login screen or boot in recovery mode) and do the following:

```

apt-clone clone packages
apt-get purge gdm
apt-get update
apt-clone restore packages.apt-clone.tar.

```

I'm not sure about the code to repair gdm, maybe it's better to wait for a second opinion.

---

### Post by wize_gurl on 2011-05-19
I have Windows and Ubuntu on seperate partitions.

---

### Post by wize_gurl on 2011-05-26
Finally, after a lot of poking around, my system is working again !!!!!!

For the benefit of other newbies like myself, I would like to explain the process. After trying a lot of different solutions (suggested in different articles), over and over again with different variations, my Windows started to work. 

[http://en.kioskea.net/forum/affich-31177-xp-won-t-start-not-even-in-safe-mode](http://en.kioskea.net/forum/affich-31177-xp-won-t-start-not-even-in-safe-mode)
[http://www.techrepublic.com/article/10-things-you-can-do-when-windows-xp-wont-boot/6031733](http://www.techrepublic.com/article/10-things-you-can-do-when-windows-xp-wont-boot/6031733)

Ubuntu still refused to work. When I would try to login, I would see a login screen with an error message on the top saying something like, 'The Power Manager configurations are not correct, please try to contact the system administrator'. 

I tried to search about boot problems in ubuntu, and tried to apply every technique that was suggested, but nothing would work for me. I could'nt even recover my data, using the Live CD. 

Then I searched the error, given on the boot screen, and realised that this was caused to lack of space on my ubuntu. I had tried to install AVG antivirus on the system, and my system which was already low on memory couldnt handle it anymore. So through the terminal, I deleted some of the programs, and rebooted. Ubuntu started again!

[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/) 

Just curious:
Some of the other material mentioned in the other articles didnt work for me like:

> 

Even though you can't boot from your hard drive, you should still be  able to mount it and and chroot it. Follow these instructions:

Boot from the Live CD, and once at the desktop, open a terminal, at the  prompt type the following commands, pressing Enter after each one:

[LIST=1]
[*]sudo mount /dev/sda1 /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]
Reference : [http://ubuntuforums.org/showthread.php?t=1656497](http://ubuntuforums.org/showthread.php?t=1656497)

Neither did this one:

> Next - you might find copying your documents easier if you use nautilus  as root (please use this for emergencies like this only):

     Code:
     gksudo nautilus 
You can copy your documents to your Windows partition, an external hard drive, or a USB stick.

You may find it necessary to mount the partitions manually:

     Code:
     sudo mkdir /mnt/windows
sudo mount /dev/sda2 /mnt/windows 
     Code:
     sudo mkdir /mnt/ubuntu
sudo mount /dev/sda5 /mnt/ubuntu 
Reference : [http://ubuntuforums.org/showthread.php?t=1747735](http://ubuntuforums.org/showthread.php?t=1747735)

Nautilus wouldnt let me access my files on ubuntu. It only showed me the Root Folder of Live CD. In the code, the system wouldnt recognise 'mkdir' command. 
Any Guesses Why ?

---

### Post by Prince Valiant on 2011-05-26
I'm glad the system is working! For future reference, please mark the thread as solved.  Thread tools--> mark as solved.

:-D

-Val

---

