---
title: "ubuntu won't start after backup"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by brocos on 2011-05-03
Hi everyone,

I've tried to perform a full backup of my Ubuntu 10.10 desktop following the instructions from this thread [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
the problem is that it could not be completed because the backup file became too big and it filled my hard drive. As a consequence, my pc won't start. Any help with this will be much appreciated!

---

### Post by madjr on 2011-05-03
hmm, if you have a live-cd handy, you can free up the disk, insert it and move the backup somewhere else.

then it should boot normally.

also i suggest just backing up things manually if you can.

---

### Post by edm1 on 2011-05-03
Ok, i need answers to a few questions.
-Where do you get to when you start your computer? Can you access the terminal? 
-If not is it possible to start your computer in recovery mode (by clicking ESC whiles you boot and choosing the option from the grub menu)?
-How far did you get in the tutorial you posted? Did you just try to backup or did you try the recovery as well (please DONT try the recovery command)

The problem is that you copied your entire hard drive to a file called 'backup.tgz' in your root folder /. Your hard drive didnt have enough space and linux doesnt like that at all. If you can gain access to the terminal and log in then this command should delete the backup and save the day.

> sudo rm /backup.tgz

If you can't access the terminal you will have to either make or find an existing live cd/usb you might have. Boot to the live CD, as though you were install Ubuntu but click (some like) 'try ubuntu' rather than 'install'. Open the file manager and click on your computers hard drive in the places menu on the left (this should mount your computers hard drive as a folder), open the mounted hard drive and go to the root folder (may have to click the up arrow till you get there). Somewhere in the root folder should be your 'backup.tgz' file, delete it.

And dont try the backup again.

---

### Post by brocos on 2011-05-26
I have accessed the hard drive booting from a usb but it doesn't allow me to delete anything. I can see the file that's causing the problem backup.tgz but when I right-click on it the option to delete is not there. I'd need to be rooted and I tried to through the shell but it didn't work.

Any ideas?

---

### Post by Miljet on 2011-05-26
Did you remember to use sudo before the rm command?

Also, you can open a terminal and type ```
gksu nautilus
```

That will open Nautilus with root priviledges. Just be sure of what you are removing. If you delete the wrong thing, it is gone.

---

### Post by spillage2 on 2011-05-26
when in the live mode go to your terminal and run sudo nautilus and delete from there..

---

### Post by brocos on 2011-05-26
I managed to delete the file. Then I restarted and got a list of different booting options (normal, recovery mode), I chose normal (probably this was a mistake)The next screen I got said:

Install problem
The configuration defaults for GNOME power manager have not been installed correctly.
Please contact your system administrator.

And it wouldn´t go any further.

Shall I give up?

---

### Post by wildmanne39 on 2011-05-26
> **brocos said:**
> I managed to delete the file. Then I restarted and got a list of different booting options (normal, recovery mode), I chose normal (probably this was a mistake)The next screen I got said:

Install problem
The configuration defaults for GNOME power manager have not been installed correctly.
Please contact your system administrator.

And it wouldn´t go any further.

Shall I give up?
Hi, try the command in  a terminal if you are running 10.04.
```
sudo apt-get install gdm

```

---

### Post by brocos on 2011-05-26
> **wildmanne39 said:**
> Hi, try the command in  a terminal if you are running 10.04.
```
sudo apt-get install gdm

```
I´m running 10.10. I´ve tried your command booting from the live cd and it says that the newest version of gdm is already installed.

Thank you all for your help by the way. I really appreciate it.

---

### Post by wildmanne39 on 2011-05-26
> **brocos said:**
> I´m running 10.10. I´ve tried your command booting from the live cd and it says that the newest version of gdm is already installed.

Thank you all for your help by the way. I really appreciate it.
Hi, from a live cd that was probably only reading the live cd. Can you get the recovery console this is how to   [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode) into recovery. when you boot choose root prompt with network 
```
apt-get update && apt-get install ubuntu-desktop && apt-getupgrade && reboot
```

---

