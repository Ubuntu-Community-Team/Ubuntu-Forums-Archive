---
title: "Can't connect at school Broadcom WLAN"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by bigbri on 2007-03-06
After 10 days troubleshooting my wireless, I am finally asking for help.  (Just imagine how far I will drive around before I ask for directions)  

I am truly at my wit's end.  The limited amount of work I've done in Linux has been cool, but if I can't use it on campus it's worthless to me.  

The short version is that I can connect at home but the connection at school drops intermittenly and then fails to reconnect.  The MIS dept at school will support Macs and Win, but not Linux.  

**_My Laptop:_** 

HP zd7140us
BCM4306
Dual Boot w/ WinXP

hda1	NTFS WinXP boot
hda2	ext3 Linux root - Edgy 2.6.17-11-generic
hda5	Linux swap
hda6	ext2 mounted /home (and IFS My Documents)

**_Driver Versions:_** all from hp.com - all work in Win

3.70.12.0
3.100.65.1
4.40.19.0
4.100.15.5

**_Home network_**
Linksys router w/ WPA

**_School network_**
Commercial setup 802.11b/g w/ no encryption (Vernier captive portal authentication)

***Attempt 1: ***ndiswrapper - poorly written directions on a forum.  Hosed my installation.  Reinstall

***Attempt 2:*** bcm43xx - used fwcutter v005? Binary downloaded through synaptic, and Network Manager.  Fwcutter would not cut any of the drivers except for 3.70.12.0, and it threw the "Don't use old drivers" error while cutting it.  Despite the error, it connected flawlessly at home.  WiFi status LED and Signal strength meter in Network Manger did not work.  Connection was intermittent at school.  It would work for a few minutes, and then drop.  The timing of the drop was always correlated with a network activity such as loading a web page or sending a ping.  As time passed, the time connected to the network was shorter each time, and the time to re-connect was longer each time, until eventually it would not connect at all.  Incidentally, a bad printer driver .deb file hosed my installation and forced another reinstall.

***Attempt 3:*** ndiswrapper v. 1.8.  I carefully followed all the directions.  It worked with the most recent driver - 4.100.15.5 - It connected flawlessly at home.  The WiFi indicator LED and signal strength in Network Manager worked flawlessly.  When I brought it to school, it wouldn't even connect to the network at all.  I tried to uninstall ndiswrapper and re-configure bcm43xx, but then I couldn't connect to anything.  I reinstalled linux to save myself the stress of troubleshooting.

***Attempt 4:*** I compiled and installed fwcutter v. 006.  It was able to cut firmware from all of the above drivers, but the only firmware that actually works with the driver is the 3.70.12.0 version.  So now I am back to my problem in Attempt 2.  Great connection at home, crappy and unusable connection at school.

---

### Post by teaker1s on 2007-03-06
use ndiswrapper and look at link in my signature

---

