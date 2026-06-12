---
title: "HELP: Problem Booting Ubuntu 11.04"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by Jacub on 2011-07-06
So I decided yesterday to  completely ditch Windows and install Ubuntu 11.04 on my system when I  faced a recurring  problem even after 3 attempts of a fresh re-install  of the OS.


  Before I go any further, please keep in mind that I am a Linux noob  with no command line or proper Ubuntu GUI experience. I have only  attempted live boots before which have been successful.


  My problem:
  I burned an ISO image of Ubuntu 11.04 (32-bit) on a CD, while making  sure to run it at the slowest possible speed, and then ran a live boot  of the OS. All seemed well so I followed the installation instructions  and chose the option of replacing WinXP with Ubuntu. Once the  installation was done, I was asked to remove the CD from the tray and  press "Enter" to proceed with system restart only to have my PC stop the  boot sequence with a black screen and a non-responsive blinking cursor.  This happens right after the motherboard splash screen/BIOS check. I  attempt a hard reset with the same result.


  So I did the following:
  
[LIST]
[*]checked the BIOS' boot sequence and everything was in perfect order.
[*]did another live boot off the CD and ran the "system check", it  showed no errors with my internal HDDs, audio output or graphic  resolutions tests.
[*]therefore went for a fresh Ubuntu re-install only to face the same  problem with the black screen and blinking cursor after booting.
[/LIST]
   I have gone through a few posts with almost the same problem as mine  where the recommended solution was to load safe mode, by pressing "e" or  holding down "shift" during boot, but it didn't work with me and I'd  still be stuck on the black screen.
  

System specs:
  ASUS M2N32-SLI Deluxe/Wireless Edition
  AMD Athlon 64
  nVidia GeForce 8400
  2 GB RAM
  Internal HDDs 40GB (used this for WinXP and Ubuntu), 120GB, 500GB
  

I would greatly appreciate any advice to help me fix this problem. Thank you for your time.


**EDIT:** Ok so I fixed my problem (YAY!). I assumed the option of a faulty  install/CD and decided to boot off a USB stick. So I created the pen  drive and commenced with another fresh installation of Ubuntu 11.04. I  rebooted when prompted after completing installation and got into the  BIOS to reset my PC's boot sequence; I disabled the option of booting  from the CD-ROM dirve as a first option, disabled booting off the USB  and set it to boot off my HDD.

 Exited and saved changes to BIOS and crossed my fingers (and toes)......IT'S ALIVE!!!


  So whatever I did got it working with only a minor issue with a  corrupted ubuntu splash screen which I got fixed by installing OS  updates and the latest nVidia driver.

---

### Post by androssofer on 2011-07-06
try installing 10.10 and running it, its more stable than 11.04, aside from tht i dont know...

---

### Post by wildmanne39 on 2011-07-06
> **Jacub said:**
> So I decided yesterday to  completely ditch Windows and install Ubuntu 11.04 on my system when I  faced a recurring  problem even after 3 attempts of a fresh re-install  of the OS.


  Before I go any further, please keep in mind that I am a Linux noob  with no command line or proper Ubuntu GUI experience. I have only  attempted live boots before which have been successful.


  My problem:
  I burned an ISO image of Ubuntu 11.04 (32-bit) on a CD, while making  sure to run it at the slowest possible speed, and then ran a live boot  of the OS. All seemed well so I followed the installation instructions  and chose the option of replacing WinXP with Ubuntu. Once the  installation was done, I was asked to remove the CD from the tray and  press "Enter" to proceed with system restart only to have my PC stop the  boot sequence with a black screen and a non-responsive blinking cursor.  This happens right after the motherboard splash screen/BIOS check. I  attempt a hard reset with the same result.


  So I did the following:
  
[LIST]
[*]checked the BIOS' boot sequence and everything was in perfect order.
[*]did another live boot off the CD and ran the "system check", it  showed no errors with my internal HDDs, audio output or graphic  resolutions tests.
[*]therefore went for a fresh Ubuntu re-install only to face the same  problem with the black screen and blinking cursor after booting.
[/LIST]
   I have gone through a few posts with almost the same problem as mine  where the recommended solution was to load safe mode, by pressing "e" or  holding down "shift" during boot, but it didn't work with me and I'd  still be stuck on the black screen.
  

System specs:
  ASUS M2N32-SLI Deluxe/Wireless Edition
  AMD Athlon 64
  nVidia GeForce 8400
  2 GB RAM
  Internal HDDs 40GB (used this for WinXP and Ubuntu), 120GB, 500GB
  

I would greatly appreciate any advice to help me fix this problem. Thank you for your time.
Here is a link that should get you into ubuntu, then you can install your nvidia driver in additional drivers and you should be ok.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
these are very good instructions if you follow then you should be ok, if you need more help post back here.

---

### Post by Jacub on 2011-07-06
> **androssofer said:**
> try installing 10.10 and running it, its more stable than 11.04, aside from tht i dont know...

Oh I forgot to mention that. I did also try overwriting the 11.04 with 10.10 but got an error (after trying twice); something about possibly having a faulty HDD or CD...etc

---

### Post by kamakazi20012 on 2011-07-06
Try following wildmanne39's advice about getting and installing nVidia drivers.  I am having a similar experience with an eMachine desktop with a GeForce 4 on-board.  Like yourself, I am new to Linux and Ubuntu and do not know the commands for a command line.

---

### Post by Jacub on 2011-07-06
> **wildmanne39 said:**
> Here is a link that will should get you into ubuntu, then you can install your nvidia driver in additional drivers and you should be ok.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
these are very good instructions if you follow then you should be ok, if you need more help post back here.

Thank you. I will definitely try the stuff mentioned under that thread.

---

### Post by BlauFusion on 2012-03-15
> **Jacub said:**
> Thank you. I will definitely try the stuff mentioned under that thread.
In case anyone else finds this thread, I managed to install ubuntu 11.10 on an old emachines computer by using the link recommended here, and using the option "acpi=off".

---

