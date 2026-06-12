---
title: "Changing Out Machines"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by zzyzx1 on 2009-10-21
I started my adventure into Ubuntu at the beginning of 9.04 on an old Dell Dimension 2350. Well, things went so good and I found all the right hacks to make life sweet. Now Im looking to make the leap to a new machine and move up to 9.10. Im still somewhat of a beginner but am looking for a reliable way to either clone or move my current world of perfection to a new box. Has anyone had success in doing this or is it best to re-build from scratch?

Thanks.

---

### Post by KhanTG on 2009-10-21
I successfully transfered the HDD from one machine to another machine, without any difficulties.  They were both laptops from different manufacturers, and it was an IDE HDD... I also use a 250GB USB HDD for diagnostics on other machines (still testing this one, but it's working thus far).

  I don't think that you'll have any issues, but if you are worried about it... you could try copying your /home folder to the new machine. I hear that that will take our settings and docs with you to a new install.

---

### Post by howefield on 2009-10-21
You could clone your old disk but I'd think you may run into issues.

For me, a new machine means a new install. Clean from the get go. Then you know any issues you run into directly relate to the machine/install in question.

---

### Post by zzyzx1 on 2009-10-21
I totally agree with both... I was smart enough to save most of my hacks in a file so I could at least get some of the love back... but im REALLY looking for smoothness on KK... dont really want to rock the boat if you know what i mean. Thank you for the feedback, i will see what others suggest.

---

### Post by pgar23 on 2009-10-21
Back-In-Time backup utility. Back up whatever files and info that you have saved. Install Ubuntu on new machine. Download Back-In-Time on new machine, restore the files and info from old machine to the new machine. TOO SIMPLE EH?

---

### Post by zzyzx1 on 2009-10-21
Sounds good. Im not so concerned with data (files, apps, etc) as much as I am concerned with sys config. Would be nice to catch all in one swoop...

---

### Post by mapes12 on 2009-10-22
I did the same as you and to copy my old HDD to the new HDD I installed the old HDD into the new machine and used the dd command to copy across the entire drive. I did it like this:

To make an exact copy of a drive install the new drive as slave and the old HDD as master. Then boot from a Live CD. UBU or something like Gparted that will get you to a Terminal prompt. Go to Terminal and enter:
```
dd if=/dev/sda of=/dev/sdb
```
#where sda is the old drive and sdb is the new drive. Then disconnect sda from its IDE channel, connect sdb into sda's IDE channel (thus making it sda). And vice versa for sdb. Boot from a Gparted Live CD. Format sdb (the old HDD) and use it as extra storage. Reboot, removing the Live CD and everything will boot from the new HDD.

---

### Post by tarps87 on 2009-10-22
I haven't had any problems so far, you may experience problems if your hardware is not supported but you would experience these with a clean install too.
If you don't want move any hard drives about you can clone the hard drive over the network, there is a how to in this thread
[http://ubuntuforums.org/showpost.php?p=7814543&postcount=12](http://ubuntuforums.org/showpost.php?p=7814543&postcount=12)
[http://ubuntuforums.org/showthread.php?t=1244282](http://ubuntuforums.org/showthread.php?t=1244282)
Although I fear I killed the thread.

If you can move the hard drives **mapes12** post will be the quickest way. Just make sure if=*drive* is the old hard drive.

---

### Post by zzyzx1 on 2009-10-22
Awesome, great stuff... So I will plan on using a new Dell machine (in hopes that the hw should be familiar) and I may add a Hauppauge and try some MythTV out once stability is confirmed. This will be greatness to not have to re-do all my hacks... cheers guys!

---

### Post by tarps87 on 2009-10-22
Here's a good guide for mythtv:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
I used it to set my TV card

---

### Post by zzyzx1 on 2009-10-22
Great link, thank you!

---

### Post by LewRockwell on 2009-10-22
> **zzyzx1 said:**
> I started my adventure into Ubuntu at the beginning of 9.04 on an old Dell Dimension 2350. Well, things went so good and I found all the right hacks to make life sweet. Now Im looking to make the leap to a new machine and move up to 9.10. Im still somewhat of a beginner but am looking for a reliable way to either clone or move my current world of perfection to a new box. Has anyone had success in doing this or is it best to re-build from scratch?

make a backup

dd your current OS

partition as desired

make an additional fresh install on a separate partition to compare with the cloned/moved copy

then if and when you want...you can test out 9.10 on another separate partition

you can also try out other *nix distros in similar fashion


You can check out a couple of our multi-boot daily beaters at these links:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.

---

### Post by kimda on 2009-10-22
This is how I reinstall or install on a new machine with previous settings: 

Backup the following directories: 
/etc    - contains system settings like your apt update sources. 
/home   - all the users settings 

If you run databases like mysql or the apache webserver i would also backup /var - for most users probably not nessesary. 

How to backup? I use tar to backup these folders, like 
sudo tar -cf home.tar /home 
sudo tar -cf etc.tar /etc 

If you got a massive home dir you could also compress it like this 
sudo tar -zcf home.tgz /home

backup your crontabs - if you use crontabs: 
sudo cp /var/spool/cron/crontabs/ . 

dump your current programs to file

dpkg --get-selections > packages  

Backup all above to external disk or something else:

Then I install ubuntu on the new system or the same machine. 

After installing: 
Copy backups to new machine.

install all the same programs again:
sudo dpkg --set-selections < packages
sudo apt-get dselect-upgrade

Now it will install all the previous installed packages. 

I allways unpack the /home and /etc backups in a seperate folder (if you run the same version on the new machine you can probably copy it over the newly installed version). Lets say /home/restore (sudo mkdir /home/restore). From there I will restore all the stuff I need.

How to unpack:

sudo tar -xf etc.tar   - for tar file
sudo tar -zxf etc.tgz  - for tgz file

---

### Post by zzyzx1 on 2009-10-22
OK, so its sounds like this is generally do-able and that others have had pretty successful results. I have kept the current system very clean of apps and data (running a Dlink NAS for storage and auto-mounting as a share) so there wont be much to move. Awesome!

---

### Post by kimda on 2009-10-22
Backing up Linux is pretty easy once you know where everything is stored. :)

---

### Post by tarps87 on 2009-10-22
> **kimda said:**
> Backing up Linux is pretty easy once you know where everything is stored. :)

On the storage medium :)

---

