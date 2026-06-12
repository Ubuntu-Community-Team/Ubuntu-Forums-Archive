---
title: "BCM4306 problems"
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by mcerisano on 2014-04-13
I have a Dell Precision Workstation T3500 with a Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) installed in it. I have been trying for two days to get my freshly installed xubuntu 13.10 to see it! I've read hundreds of message boards and forums but all solutions seem to fail. Could you please list the terminal commands needed to get this to work. It is very important that I get this working by tomorrow morning.

Attached is the results of running Wireless_Script on my computer...

THANK YOU in advance for your time and knowledge!

---

### Post by mörgæs on 2014-04-13
As a 101'st attempt I suggest reading the sticky note on Broadcom.

---

### Post by varunendra on 2014-04-13
The solution is suggested in the Broadcom troubleshooting sticky of this section of the forums. I am basically just repeating it here -

Please open a terminal (Ctrl-Alt-T) and run the following commands to install the required firmware for the native driver, and purge the sta driver that you are currently using -
```
sudo apt-get install linux-firmware-nonfree
sudo apt-get purge bcmwl-kernel-source
```
Reboot and see if you can see available networks and connect to them now. If not, please post a fresh report of the wireless_script.

---

### Post by mcerisano on 2014-04-13
I ran the command you suggested...

michael@michael-Precision-WorkStation-T3500:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following package was automatically installed and is no longer required:
  linux-image-generic
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
michael@michael-Precision-WorkStation-T3500:~$ sudo apt-get purge bcmwl-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernal-source

and ran the wireless_script again...

---

### Post by mcerisano on 2014-04-13
Still not working... See previous post.

---

### Post by Hadaka on 2014-04-13
hi, give this a try
```
sudo modprobe -rf wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..*From a wired conection ,connected to the internet
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree
sudo modprobe -rf b43
sudo modprobe b43
```

---

### Post by varunendra on 2014-04-13
There was a mistake in your purge command -
> **mcerisano said:**
> ....
E: Unable to locate package **bcmwl-kern[COLOR="#FF0000"]a[/COLOR]l-source**
....

It is "..kern**[COLOR="#0000FF"]e[/COLOR]**l..", not "kern**[COLOR="#FF0000"]a[/COLOR]**l"

---

### Post by mcerisano on 2014-04-13
Sorry for the delay... Had to reinstall xubuntu again! After fresh install opened terminal window and enter the two commands:

sudo apt-get install linux-firmware-nonfree
sudo apt-get purge bcmwl-kernel-source

Spelling Kernel correctly this time!!! And everything works perfectly!!!

THANK YOU THANK YOU THANK YOU

---

### Post by varunendra on 2014-04-13
You're welcome ! :)

Please mark the thread as [SOLVED] using "Thread Tools" link above the top post.

---

