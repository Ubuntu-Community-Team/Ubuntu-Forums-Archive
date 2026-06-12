---
title: "Installing the ra2570 driver..."
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by VitalBodies on 2008-05-23
How does one install that driver or do I need to? 

I have tried so many things for so many days...
I have a wUSB56gv4 and think I need the rt2570 driver.

I got the impression this was some how a part of Ubuntu 8.04. 
I am using the 64-bit desktop edition of UbuntuStudio.

EDIT: The problem, it seems, is I was using UbuntuStudio rather than Ubuntu. 
This prevented a number of things from installing or running correctly. I switched to Ubuntu 64-bit and all when well...

I do NOT know why the default rt2500usb driver does not work right. 
I could connect but the connection while always connected would be fast then painfully slow. Mostly slow... I would like to use the default drive if I can.

---

### Post by VitalBodies on 2008-05-25
I got the wusb56gv4 working by installing the legacy driver:

**SHORTENED INSTRUCTIONS:** 
Download to desktop: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
Extract the driver (right click on its icon on your desktop and select "Extract Here.")
sudo apt-get install build-essential
cd ~/Desktop/rt2570-cvs-**2008052414**/Module **(must = Folder Name)**
make
sudo make install
sudo gedit /etc/modprobe.d/blacklist 
#Added these entries to the blacklist to replace rt2500usb with rt2570usb: 
blacklist rt2500usb
blacklist RT2500USB

sudo modprobe rt2570
sudo ifconfig rausb0 up
REBOOTED then set networking to manual (used my routers setting SSID etc) rather than roaming and REBOOTED
sudo ifconfig rausb0 up
REBOOTED
Connected!

NOTE: You should keep these instructions on hand on your computer, as you will not be able to connect to get them...
The phrase [COLOR="Red"]#(must = Folder Name)[/COLOR] should not be used in the terminal. This is only a note of instruction for you. 

**CREDITS:**
[http://ubuntuforums.org/showthread.php?t=797823]("http://ubuntuforums.org/showthread.php?t=797823")
Do not attempt what is written in that post until you get to at least the 3rd page. 

[http://ubuntuforums.org/showthread.php?t=739139]("http://ubuntuforums.org/showthread.php?t=739139") Post#8

NOTES: 
I have heard from the SerialMonkey people "Ubuntu also provides an updated rt2x00 package in backports that seemed to work for most people who had previously problems with the rt2x00 driver installed during the regular installation".

**Backports:** [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by VitalBodies on 2008-05-26
If you update the kernel (which happens doing updates) you will have to reinstall the driver. 

**SHORT REINSTALL INSTRUCTIONS:**
1.) Download to desktop: [http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz)
--> If you did not do this before updating the kernel you still might be fine. 
--> Use the latest driver you have. 
2.) Extract the driver (right click on its icon on your desktop and select "Extract Here.")
3.) cd ~/Desktop/[COLOR="Red"]rt2570-cvs-2008052612[/COLOR]/Module [COLOR="Red"]#(must = Folder Name)[/COLOR]
4.) make
5.) sudo make install
6.) sudo modprobe rt2570
7.) sudo ifconfig rausb0 up
8.) Bring up the program RutilT and connect as needed...
9.) You should be Connected!

NOTE: You should keep these instructions on hand on your computer, as you will not be able to connect to get them...
You should keep the driver you download until you download another also for the same reason...
The phrase [COLOR="Red"]#(must = Folder Name)[/COLOR] should not be used in the terminal. This is only a note of instruction for you.

---

### Post by VitalBodies on 2008-05-26
**USEFUL LINKS: **
[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")
[http://rt2x00.serialmonkey.com/]("http://rt2x00.serialmonkey.com/")

NOTES: 
I have heard from the SerialMonkey people "Ubuntu also provides an updated rt2x00 package in backports that seemed to work for most people who had previously problems with the rt2x00 driver installed during the regular installation".

**Backports:** [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

If anyone confirms the backports works, for this driver, and how to make this work please show us...


This device is also said to work out of the box: 
[http://www.edimax.com/en/support_detail.php?pl1_id=1&pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pd_id=8](http://www.edimax.com/en/support_detail.php?pl1_id=1&pl1_idSelect=support.php%3Fpl1_id%3D1%26mwsp%3D1&pd_id=8)

---

