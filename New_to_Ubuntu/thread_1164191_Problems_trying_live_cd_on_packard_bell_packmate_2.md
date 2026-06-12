---
title: "Problems trying live cd on packard bell packmate 2330"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by darkvellardo on 2009-05-19
When i tried ubuntu live cd it goes to the menu screen and when i click on "try ubuntu without altering windows" then it tries to load up, but the screen remains blank and the cd reader stops reading the cd. 

I'm trying to install the 9.04 version and also i've tried to install it in safe graphics mode with the same results

My specs are:
Processor: Intel® Core ™ Duo Processor T2330 (1,6Ghz / 1024Kb caché L2)
Memory: 2 Gb DDR2
HDD: 160 GB SATA
Video: SIS Mirage 3 graphics
Audio: Realtek HD audio
Wlan: Realtek RTL8187B

---

### Post by Niniel on 2009-05-19
Your CD is probably bad. Try burning a new one. Also make sure the downloaded iso is ok (it usually is, but check anyway) by computing its MD5 checksum - in the terminal, go to the directory where the iso is located (e.g. /home/user name/Desktop) and type "md5 filename.iso" - and comparing it to the checksum posted on the download page.
You may have to try several times until you get a good CD.

---

### Post by mapes12 on 2009-05-19
> **darkvellardo said:**
> When i tried ubuntu live cd it goes to the menu screen and when i click on "try ubuntu without altering windows" then it tries to load up, but the screen remains blank and the cd reader stops reading the cd. 

I'm trying to install the 9.04 version and also i've tried to install it in safe graphics mode with the same results

My specs are:
Processor: Intel® Core ™ Duo Processor T2330 (1,6Ghz / 1024Kb caché L2)
Memory: 2 Gb DDR2
HDD: 160 GB SATA
Video: SIS Mirage 3 graphics
Audio: Realtek HD audio
Wlan: Realtek RTL8187B
I had the same problem with one of my machines. Using the [alternate installation CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") solved the problem and loaded Ubu without a hitch.

---

### Post by Aaardwark on 2009-05-19
There is a feature in the menu to check if the cd is corrupted. I recommend using that feature the first time you've burned a new Ubuntu disc. It's really annoying if something is corrupted during install. Afterwards you can use the same disc to do multiple installs.

Make sure you burn OS discs at slowest available speed, to avoid corruption. That said, if it turns out the disc isn't corrupted, the alternate install or the latest LTS could be viable options.

---

### Post by Aaardwark on 2009-05-19
It could also be because of the graphics card:
[http://ubuntuforums.org/showthread.php?t=615094]("http://ubuntuforums.org/showthread.php?t=615094")

---

