---
title: "Broadcom 4318 driver problems in Ubuntu"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by n00b54 on 2007-02-07
Machine specs:
 
HP dv4405nr Pavilion notebook
1.5GHz Celeron M
1.2 GB RAM
Wireless Card: Broadcom BCM 4318 [Air Force One 54G]
OS: Dual boot between Ubuntu Edgy and XP Pro


In the transition from confident Windows user into the unfamiliar world of Linux, I can't seem to solve one of the fundamental issues - wireless card driver. 

Ubuntu simply does not communicate with the wireless card, as it does not appear in the Network Settings, and the card light refuses to come on (common problem with a wireless card with Windows drivers). 

Following the advice of countless forums, I have attempted two distinct processes to fix the problem:

1) Install the "fw-cutter" package, which supposedly sucks the firmware out of a .o file (readily available for download) and places it into the firmware directory.  All commands were completed successfully, but never succeeded in allowing the OS to communicate with the card. 

2) Use "ndiswrapper", along with the Windows .inf & .sys files to 'trick' Edgy into working with the card.  After finding the original driver files in the Windows partition, I once again followed this process with every command seeming to work perfectly.      

Neither has had any effect, and the card still shows up in the Device Manager as a PCI device, but is not recognized as a network connection through the default GUI or Network-Manager (also an attempt for this problem). 

Any thoughts?  Help is appreciated!

---

### Post by oz1980 on 2007-02-08
did you remember to remove the old driver and firmware before using ndiswrapper. I had a problem were my bcm4318 was set up with both, and It would try to go the firmware route first. I had to do this:

sudo rmmod bcm43xx

This removed the firmware module. then I re-installed the driver with ndiswrapper. (I got spoiled with the gui version tonight). Then It connected great, and when I rebooted, it still worked. My problem was that the connection would drop if I was in another room in my appartment. It did that in windows. I was using Suse, and ndiswrapper solved the issue. I tried the firmware when I switched to Ubuntu, and it started to drop the signal again. I think it is something wrong with the firmware. But ndiswrapper is working great.You may actually have to remove the files in the firmware directory to keep it from comming up again too. Also, If you have your ethernet port enabled, then all your tcp may be trying that route and finding a dead end.

To recap:

1. remove the bcm43xx module and fimware. (sudo rmmod bcm43xx; rm /lib/firmware/*/*; rmdir /lib/firmware/*; rm /lb/firmware/* (incert folders and files when needed))
2. disable other network devices (sudo ifconfig eth0 down)
3 re-install driver with ndiswrapper ndiswrapper -i ~/path/bcml5.inf)
4. enable wireless device (if it didn't come up already) (modprobe ndiswrapper; ifconfig wlan0 up)

---

### Post by ukripper on 2007-02-08
> **n00b54 said:**
> Machine specs:
 
HP dv4405nr Pavilion notebook
1.5GHz Celeron M
1.2 GB RAM
Wireless Card: Broadcom BCM 4318 [Air Force One 54G]
OS: Dual boot between Ubuntu Edgy and XP Pro


In the transition from confident Windows user into the unfamiliar world of Linux, I can't seem to solve one of the fundamental issues - wireless card driver. 

Ubuntu simply does not communicate with the wireless card, as it does not appear in the Network Settings, and the card light refuses to come on (common problem with a wireless card with Windows drivers). 

Following the advice of countless forums, I have attempted two distinct processes to fix the problem:

1) Install the "fw-cutter" package, which supposedly sucks the firmware out of a .o file (readily available for download) and places it into the firmware directory.  All commands were completed successfully, but never succeeded in allowing the OS to communicate with the card. 

2) Use "ndiswrapper", along with the Windows .inf & .sys files to 'trick' Edgy into working with the card.  After finding the original driver files in the Windows partition, I once again followed this process with every command seeming to work perfectly.      

Neither has had any effect, and the card still shows up in the Device Manager as a PCI device, but is not recognized as a network connection through the default GUI or Network-Manager (also an attempt for this problem). 

Any thoughts?  Help is appreciated!




If you have bcm4318  then definitely I recommend :KS follow this  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)  guide as instructed and you won't have any problems with your wireless card anymore. It took me 2 minutes to setup my wireless card on my acer 3003lmi with bcm4318 yesterday, hope it is helpful.

---

### Post by n00b54 on 2007-02-09
> **ukripper said:**
> If you have bcm4318  then definitely I recommend :KS follow this  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)  guide as instructed and you won't have any problems with your wireless card anymore. It took me 2 minutes to setup my wireless card on my acer 3003lmi with bcm4318 yesterday, hope it is helpful.

AMAZING!  This actually fixed my problem...  

It seemed the main step I was lacking was: 

# If you are using 64bit Edgy Eft and the 2.6.17-10-generic, make sure you are NOT using the 2.6.17-10-generic kernel as it doesn't work (after running the script, you will be warned if there is a problem). If you need help finding a different kernel, check here.
# If you have issues with Network Manager, make sure that all lines in /etc/network/interfaces that have anything except the word (interface) LO in them are commented out (have a # in front of them) or do not exist (the installation script should have removed them)
# If you are having issues, try running, in this order, one at a time:
Code:

sudo rmmod bcm43xx sudo rmmod ndiswrapper sudo modprobe ndiswrapper sudo ifdown eth1 sudo ifup eth1 sudo dhclient


Thanks for the help!

---

### Post by ukripper on 2007-02-09
I am glad it helped you.:)

---

