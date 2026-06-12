---
title: "Linksys WMP54G Troubles"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by drbob07 on 2007-04-09
I have a Linksys WMP54G (v4.1) with the RT2500 chipset.

I've tried numerous guides on how to configure it to work with WPA.

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Both of those wielded the same result. I got Gnome-Network Manager working with my wireless card. But the menu for selecting encryption shows None, WEP 64 and WEP 128... No WPA :((

I then tried this guide
[http://ubuntuforums.org/showthread.php?p=1500082](http://ubuntuforums.org/showthread.php?p=1500082)
Which failed completely.


Anyways, I'm sitting on my network completely unsecured right now as WEP doesn't seem to get along with me :'/


So is there any other ways to get WPA working or should I just give up and use WEP...


Linksys WMP54G v4.1 RT2500 -- PCI Card
ZOOM ADSL X6 Modem/Router/Wireless AP

Also, I tried installing the NDISWRAPPER, it doesn't seem to work. The driver is installed, but it doesn't say it detected the hardware.

(Figured NDISWrapper was worth a shot, as opposed to what comes preinstalled in Ubuntu)

(Thanks in advance)

---

### Post by Redandtheblue on 2007-04-09
I am having trouble as well with this.  I cannot seem to get this to get either of the methods to work.

---

### Post by thebluejay on 2007-04-10
same problem: the wireless connection works fine with no encryption, but fails when WEP is enabled. The connection to the router appears to be activated, but no internet connection is possible.

---

### Post by cielo23 on 2007-06-12
I've been working on this issue for the last two weeks with the WMP54G v4.1 and a Westell wireless gateway ( also tried a Linksys  wifi router ).  The card is seeing the wireless network at near 100%, but it just won't make the connection....I've tried blacklisting the rt61pci module, using ndiswrapper and changing the interfaces file but nothing works!! Help!

---

### Post by chris86wm on 2007-06-29
Well I haven't gotten my WMP54G v4.1 to work with WPA, however it does work with WEP and unencrypted networks (feisty).

I had to uninstall the Network Manager applet, and then manually setup my card using the network settings found in System=>Administration=>Network.
I also disabled my onboard ethernet using that menu, but I'm not sure if thats necessary.

I'm going to keep tweaking around with it to get WPA working, because WEP just doesn't cut it in my book. Will post back here if i find anything.

---

### Post by DO55 on 2007-07-04
from April 9th, 2007 and still dose not work !?

i will back to windows then

---

### Post by kevdog on 2007-07-05
Did you guys try compiling the serialmonkey cvs drivers for the rt2500 and using these?  To the best of my knowledge, compiling these drivers as a replacement for the earlier built in versions in ubuntu, result in the system working better.  Ive also had other tell me that after installing wpasupplicant, that wpa will work, although again all configurations need to be made in the /etc/network/interfaces file.  Networkmanager does not work well with rt2500.  If a GUI is needed, compilation and installation of the rutil is needed.  This from what I heard also works nicely.

---

