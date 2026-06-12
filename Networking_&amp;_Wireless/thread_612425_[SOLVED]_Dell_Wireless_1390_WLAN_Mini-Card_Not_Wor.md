---
title: "[SOLVED] Dell Wireless 1390 WLAN Mini-Card Not Working"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by Sam Plamondon on 2007-11-13
Hello, my Dell Wireless 1390 WLAN Mini-Card, or as Ubuntu's Terminal it, the "Broadcom Corporation BCM94311MCG wlan mini-pci 9 (rev 01)", is not working.  I am running Ubuntu 7.10 "Gutsy Gibbon", the Desktop x86 version.
I installed "ndiswrapper-common" and "ndiswrapper-utils-1.9" (both version "1.43-1ubuntu2") from Synaptics Package Manager using the Ubuntu installation CD (I have absolutely no internet connection on Ubuntu).  I then got the wireless card's driver ("R151520.exe") from Dell's official site and transferred it by USB to Ubuntu, where I saved it in "/root/.drivers/wifi".  I then extracted the driver's files and located the "bcmwl6.inf" file at "/root/.drivers/wifi/R151520.exe_FILES/DRIVER".  Other files in this folder were "bcm43xx.cat", "bcm43xx64.cat", "bcmwl6.sys", and "bcmwl664.sys".
I then inputted this in the Terminal and received these responses:

===== $sudo ndiswrapper -i ~/.driver/wifi/R151520.exe_FILES/DRIVER/bcmwl6.inf
===== [driver bcmwl6 is already installed] (I might have installed it on an earlier try.)
===== $sudo ndiswrapper -l
===== [bcmwl5 : invalid driver!]
===== [bcmwl6 : invalid driver!]
===== [r151520.exe : invalid driver!]

So now I am stuck.  Does anyone see any problems or errors with my methods, and if not, are there alternate ways to get my wireless card working (I cannot directly connect the Internet to Ubuntu, but I can get files from my Windows partition or other computers and transfer them by USB)?
Take to mind that I have been trying out Ubuntu for less than a week, and have no past experience with Linux or using commands in the Terminal.  Please explain in a way that a newcomer like me can understand!
Thank you for reading this through.

---

### Post by moneyman1978 on 2007-11-14
for me to install my ndiswrapper drivers i did a
ndiswrapper -i bcmwl5.inf
followed by
ndiswrapper -m
ndiswrapper -ma
ndiswrapper -mi

And it all worked for me. To unistall the drivers i would do a 
ndiswrappper -r bcmwl5


All of my drivers work for my card but only thing that i cannot connect to are wireless lans where the SSID is hidded with WPA2 ecyption could be somthing to do with wpa_supplicant.

---

### Post by moneyman1978 on 2007-11-14
Double post

---

### Post by Sam Plamondon on 2007-11-15
Well, I re-installed Ubuntu 7.10 and followed the instructions at this thread:  "http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+wireless".  My wireless card now works.

---

