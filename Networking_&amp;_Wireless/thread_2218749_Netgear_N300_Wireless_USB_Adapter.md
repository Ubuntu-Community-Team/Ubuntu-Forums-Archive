---
title: "Netgear N300 Wireless USB Adapter"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by Yhuzan on 2014-04-21
Hello, I just installed and am actively using Ubuntu (14.04) for the very first time today on a cheap HTPC for my parents.

Given that it is an HTPC, it is in the living room and I don't have an Ethernet cord long enough to reach it, thus I am trying to use a N300 Wireless USB Adapter (Netgear). However, the included resource CD (WNA3100) is not working and I have no idea on what to do.

I just need the drivers to get the USB device up and running so I can get connected to the internet. Thorough instructions on how to install them, too, would be greatly appreciated, as I have no idea on how to use the archive manager.

Any help would be greatly appreciated,
Yhuzan

---

### Post by mintyninja41 on 2014-04-21
Hi Yhuzan,

Right, so the problem is a missing driver for a WiFi device.  That being the case, I suggest that you check out what this website has to offer, if you haven't already: ["]http://wireless.kernel.org]("http://wireless.kernel.org)

If not there, you may want to use a search engine (I prefer Google) to locate a driver for ubuntu.  If you cannot find this, even after trawling through the internet for a while, you'll be forced to track down a driver for Microsoft Windows and use that with NDISwrapper.  See the corresponding page in the Ubuntu Documentation: ["]https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Once you locate a driver file (whether written for Microsoft Windows or Linux), save it to a USB drive, plug the USB drive into the HTPC and set up the driver from there.

NOTE: While drivers aren't my strong suit, I still recommend that you avoid NDISwrapper unless there is no alternative.  NDISwrapper (as I understand it) has been reported several times as functional, but very slow in daily usage.  

If you have any more problems, I'd be happy to help in any way I can.

Thanks,
Minty

---

### Post by Yhuzan on 2014-04-21
Thanks for your response!

I found other responses ([http://askubuntu.com/questions/372705/netgear-n300-wna3100-install-ubuntu-13-04](http://askubuntu.com/questions/372705/netgear-n300-wna3100-install-ubuntu-13-04)) but they talk about Wine and Ndiswrapper, too. Following your link (which is apparently broken if I click it but works fine if I highlight it and click "go to"), there isn't a version for 14.04 Trusty Tahr listed in the downloads. Which version should I download if I go that route?

Edit: Ironically, I just tried a Belkin USB stick I had laying around and it connected to my wi-fi network no problem, no drivers required, lol. So, my driver problem is fixed, however I'm still curious about Ndiswrapper.

Thanks for your time,
Yhuzan.

---

### Post by kurt18947 on 2014-04-22
From what I understand, getting the Netgear WNA3100 and particularly the WNA3100v2 to work with linux are good skills building exercises.  If you can get them working you have accomplished something, they have a reputation as 'problem children'.  As you have discovered, it's simpler to use hardware that works 'out of the box'.

---

### Post by garyzw on 2014-04-23
This is a working guide for anyone looking for a comprenhensive way to install the driver for a Netgear N300 WNA3100 USB wifi adapter can follow these steps:

**Install NDISWRAPPER**:
Download the latest [NDISWRAPPER source code]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page")
browse to it in terminal: cd /path/to/source/code

**In terminal add each of the following commands seperately:**
make uninstall
make
sudo make install

**Installing the driver:**
Download the wna3100 driver which is attached to this post and unzip it
Browse to the directory with the wna3100 driver: cd /path/to/driver
[B]
Now add your windows module to ndiswrapper:[/B]
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
iwconfig

If iwconfig shows that the USB device is scanning then you have installed the driver correctly and will have wireless capabilities with a minute, if not you either dont have the correct driver or its not installed correctly.

**To autostart WIFI**

open in termainal **sudo gedit /etc/modules**
    
Add **ndiswrapper** to the bottom of the list.  Save

And blacklist any conflicting drivers (my conflict was bcm43xx) to prevent conflict:

sudo nano /etc/modprobe.d/blacklist

Add &#8220;blacklist bcm43xx&#8221; in my case, to the bottom of the list. Save

This worked for me

---

