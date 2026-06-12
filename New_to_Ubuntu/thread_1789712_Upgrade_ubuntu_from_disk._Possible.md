---
title: "Upgrade ubuntu from disk. Possible?"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by vallvi on 2011-06-24
Hi,
I've Ubuntu 10.04, and I want to upgrade to 11.04. I understand that to be able to do this, I've to first upgrade to 10.10, and then to 11.04. Right? I would like to avoid a clean intall because then I'll lose all my settings, etc. 

Now, I've this horrible slow Internet connection at home (It takes half a day to download 700MB), and this really fast connection at work. So want to dowload ubuntu 10.10 and 11.04 at work, save them to a disk, and then upgrade at home from those disks. My question is: is this possible, and if so: how do I go about it?

Thnx!

---

### Post by Ufonautas on 2011-06-24
Hey, vallvi,

Just burn Ubuntu 11.04 CD at Work, then boot it at home, and choose "Install Ubuntu", then you'll see options like:

Install Ubuntu alongside Ubuntu 10,04
Upgrade Ubuntu 10.04 to 11.04
Erase and use entire Disk
Custom Settings 

(something like that), just choose Upgrade ubuntu 10.04 to 11.04, All files and most of the settings will be safe :)

---

### Post by Ufonautas on 2011-06-24
Hey, vallvi,

Just burn Ubuntu 11.04 CD at Work, then boot it at home, and choose "Install Ubuntu", then you'll see options like:

Install Ubuntu alongside Ubuntu 10,04
Upgrade Ubuntu 10.04 to 11.04
Erase and use entire Disk
Custom Settings 

(something like that), just choose Upgrade ubuntu 10.04 to 11.04, All files and most of the settings will be safe :)

---

### Post by vallvi on 2011-06-24
Thnx Ulfonautas,
I tried this with 10.10 (of which I have a disk), but it doesn't offer me the possibility to upgrade. Just: 1) install alongside, 2) entire disk, and 3) specify partition manually. 

Or is this something that would only work with 11.04?

---

### Post by Paqman on 2011-06-24
Yep, totally possible. Just not with the standard disk:

[Upgrading using the Alternate CD]("https://help.ubuntu.com/community/NattyUpgrades#Upgrading Using the Alternate CD/DVD")

Obviously it can only upgrade packages that in the main repos.

---

### Post by nerdy_kid on 2011-06-24
I would NOT try the upgrade option from the LiveCD -- it totally fried my system.  However, I think that you can go stick the cd in the drive, go into software sources, hit add volume and select the cd.  Then refresh your software sources, and upgrade...I haven't tried this though.

---

### Post by grahammechanical on 2011-06-24
When I put my 11.04 CD in the drive and hold down shift so that the disc is mounted but the installer does not run, I get this message.

> Upgrade volume detected. A distribution volume with software packages has been detected. Would you like to try to upgrade from it automatically?

I think this may be an option that started with 11.04

Regards.

---

### Post by westie457 on 2011-06-24
> **grahammechanical said:**
> When I put my 11.04 CD in the drive and hold down shift so that the disc is mounted but the installer does not run, I get this message.



I think this may be an option that started with 11.04

Regards.

Hi another way is boot into your normal system and them put the CD in the drive. If you do not get the option quoted above click on the 'Install' icon and you should get a menu with all of the options plus one to upgrade your existing installation.

---

### Post by vallvi on 2011-06-24
Thanks for all the feedback. 
I think I'll try the Pacman solution, using the alternate CD. Looks like the most 'official' way to do it.
Will let you know whether/how that works.
Thnx!

---

