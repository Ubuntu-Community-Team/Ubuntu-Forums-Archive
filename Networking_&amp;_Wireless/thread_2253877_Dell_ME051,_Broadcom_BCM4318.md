---
title: "Dell ME051, Broadcom BCM4318"
date: 2014-11-23
forum: Networking &amp; Wireless
---

### Post by Nosphky on 2014-11-23
I was given an old Dell portable -series ME051, Celeron M06D8 at 1.4 Ghz running WindowsXP.  I tried it and all seemed to work ok including wifi connection to my router.  

From a live usb of Kubuntu 1410, it was apparent that the wifi would not connect and a driver was required for the wifi card which Kubuntu identified as a 'Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Control (Wireless 1370 WLAN Mini-PCI-Card)'

Using a wired connection to my router, I successfully completed the installation of K1410 and then downloaded some 200MB updates.  Kubuntu appeared fully functional.  Using the Driver Manager in the system settings, I clicked to install a driver for the wifi.  The progress bar moved steadily to 86% and then stalled.  Modem activity (blinking lights) ceased as did disk activity.  Using the browser showed the internet connection had been lost - although my desktop machine continued to work fine on the net - so my router / modem was fine.   I waited for about half an hour - just in case.

A restart failed to complete correctly - leaving the Kubuntu logo in the centre of a dark screen and only a prolonged push on the power button would shut the pc down.  After reboot, I was unable to connect to the internet either with a wired connection or with wifi and I couldn't find a way round this.  'Driver Manager' no longer indicated that a driver was needed for the wifi card. 

I made a completely fresh installation of Kubuntu from the usb drive.  Repeated about 200 MB download of updates and tried again to download the wifi driver.  Again it stalled at 86% and my efforts mentioned above and results were identical except this time when shutting down, I had a screen-full of text with the Kubuntu logo in the centre.  Again I had to use the power button to shut down.

Does anyone have any advice on installing a driver for the wifi card ?

Thanks.

---

### Post by mörgæs on 2014-11-24
For a computer that old I wouldn't recommend Kubuntu but Lubuntu.

When you have a working and fully updated system using wired internet access you could try this:
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Hadaka on 2014-11-24
Hi,lets give it the ole try..
open a terminal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf#ignore any error
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```
boot and test wireless
if good..then do..
```
sudo apt-get update
sudo apt-get upgrade
```
thanks.
*Data entered on a series ME051  2005 dell-40 gig drive..2k ram
brcm 4318 wirless- Ubuntu 12.04 LTS

---

### Post by Nosphky on 2014-11-24
Thanks for the replies Morgaes and Hadaka.

I was able to complete the first 2 steps in Hadaka's list.  The third (sudo apt-get install b43-fwcutter firmware-b43-installer) would not work because I cannot get an internet connection.
As I said in the OP, at 86% of the driver installation, the internet connection was cut.  
This happened both times.  Whatever cut the connection (a wired connection to my router) stuffed the system 
and I cannot find anyway to get it back through 'Connection manager' or through 'Network management settings'.

What I did after the first failure was to go back to the usb stick : reboot a live version with internet connection
 and then install Kubuntu again.

It looks like I shall have to make a third install.  That'll have to wait till tomorrow.

---

### Post by Hadaka on 2014-11-24
Hi, this loads the correct driver no internet required.
be sure to download the zip file first

[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
Post #7

---

### Post by kemal2 on 2014-11-24
I'm having similar issues with a hp dv8000 running 14.04 lts
Wondering if I can try the same thing...

---

### Post by mörgæs on 2014-11-25
If you have the same wifi card then yes.

---

### Post by Nosphky on 2014-11-25
Hadaka said : --

"Hi, this loads the correct driver no internet required.
be sure to download the zip file first

[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)
Post #7 				"

I followed the instructions in the post #7 and now have /lib/firmware/b43/*  installed ok

I still cannot connect to the wifi but there is one small change.  When I click the network icon in the system tray, I now have two icons displayed : the airplane mode (disabled) and now the 'Wireless' icon.  This is the first time I have seen the wireless icon but unfortunately it is disabled and no clicking or rebooting will get it enabled.

I can however, now connect by wired connection.

---

### Post by Hadaka on 2014-11-26
Hi, now hat you can enter commands with the wired connection
please do...
```
sudo apt-get update
sudo apt-get upgrade
```
these will take some time.
when finished, boot and test wireless
thanks.

---

### Post by Nosphky on 2014-11-26
update and upgrade done ok using wired connection.  After reboot, the wireless icon still shows 'wireless disabled' and clicking on it has no effect.

---

### Post by Hadaka on 2014-11-26
Hi, click the wireless icon, then make sure the 'Enable Wireless is checked
you may also want to check the keyboard on/off by pressing the fn/f2 keys
ONE time and then entering..
```
rfkilll list all
```
if any say yes- then click it one more time and repeat.
you may also want to see if you can reset bios to default
good luck.

---

### Post by Nosphky on 2014-11-27
Hi Hadaka :

Sorry I didn't see your latest - I didn't notice that page 2 had been started on this thread.

Well, the enable wireless was disabled and wouldn't accept a check.  So I tried your suggestions : fn/f2 keys once, and rfkilll list all.  The output was :
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

and then I looked again at the icon - no more red cross, and my wifi network had been located.  A click on the connect button and a quick check with firefox shows that the wifi connection is now up and running.

I don't understand which action cleared whatever it did clear.  But thanks for sticking with the problem and helping me out.  I'm marking the thread solved.

---

### Post by jesse9498 on 2014-11-27
Alot of the older dell computers have generic wireless minicards installed that identify themselves as broadcom cards. Switching it out with an Atheros or Intel wireless card will solve the wifi issue. I never have had much luck with the driver work arounds.

---

### Post by Hadaka on 2014-11-27
Hi, glad that worked for you.
the fn/f2 key combo is the on/off keybord for wifi
so you simply turned it on and the rfkill command
reports the status.
enjoy.

---

### Post by Nosphky on 2014-12-05
FWIW, a brief update.

After a few days, I decided that Kubuntu wasn't for me so I installed UbuntuStudio 14-10.  (I am using UbuntuStudio 1404 on my desktop).

It runs just fine for what I need. And post #3 in this thread was all I needed to get the wifi running.

---

### Post by Hadaka on 2014-12-05
Great !!  glad you found something that works for you.
enjoy !

---

