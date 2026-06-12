---
title: "USR MAXg 5411"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by tsktsk on 2006-11-09
Hi all,
I'm completely satisfied with Ubuntu, except for one thing.. I cannot figure out how to make this (U.S. Robotics MAXg 5411) pcmcia wireless card work.

I am running Ubuntu Dapper Drake 6.06.1 on a IBM Thinkpad T23.

lspci produces this output:
```

0000:07:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]
802.11g Wireless LAN Controller (rev 02)

```

...but the power LED on the card is switched off and - in general - the card does not do anything.

Any help would be appreciated,
thanks in advance :D

---

### Post by Jbweld on 2006-12-06
This is My compiled references For USR MAxG 125MB Pci Card Will try this again on  PCMICA Card next...Cheers! It may work the same as Ubuntu 6.10 sees it the same.
IN TERMINAL Program...
sudo apt-get install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh
sudo apt-get install network-manager
sudo apt-get install network-manager-gnome
sudo apt-get
sudo apt-get install wpasupplicant
--------------------------------------------------------------------------
sudo gedit /etc/network/interfaces
# Comment out everything other than “lo” entries in that file and save the file 
USE # to comment out!
((Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file
Sudo Gedit /etc/default wpasupplicant))) add ENABLE=0 into it and save file.
-----------------------------------------------------------------------------
sudo touch /etc/default/wpasupplicant
YEAH RE_Boot
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
Then set it all up with wpa/network names etc..and your done.

---

### Post by ayhamzxz on 2007-04-04
danke schön

---

### Post by ayhamzxz on 2007-05-07
i dont know it doesnt work 
i ve tryed all the instructions but am finding the networks wen i open the Wireless Assistant wireless lan manager but i cant connect to the network 


can u help me plzzzzzzzzzz

---

