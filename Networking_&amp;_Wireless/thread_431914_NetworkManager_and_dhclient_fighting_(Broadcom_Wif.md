---
title: "NetworkManager and dhclient fighting? (Broadcom Wifi)"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by Maxsilver on 2007-05-03
New Ubuntu user here. I have just put a clean install of Ubuntu Fawn on a Dell Notebook with an Broadcom BCM4309 802.11abg card.

Using the tutorial here ([http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)) I got wifi working using ndiswrapper.

However, my problem is that the NetworkManager Applet doesn't seem to like ndiswrapper.

For instance, I can get my wifi card to work by typing in ...

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo dhclient

almost immeadietly, it works perfectly. Check email, grab websites, it works.

"sudo iwconfig" shows that using dhclient to connect, works as well. Lists access point, link quality, ect.

However, in NetworkManager, it only sometimes lists the Wifi spots. If it does, and I click on it, I get two green dots, and a spinning blue thingy... The tooltip says "attempting to connect to 'silver' (the wifi point) -- and it says that for a long time (until it gives up trying to connect.)

I assume my wifi card and ndiswrapper are installed properly. running "sudo ndiswrapper -l" claims my bcmwl5 driver is in installed and the device is present. And using "sudo dhclient" it will connect just fine

However, anytime the NetworkManager applet is running, it messes up this connection.

Is there any way to fix this, without disabling NetworkManager? (I have a temp fix by turning off NetworkManager in sessions, but this notebook is going to my girlfriend, who would probably not like using terminal commands to connect to wifi points and switch between wired and wireless networking)

Any help is greatly appreciated.

---

### Post by dannyboy79 on 2007-05-04
have you checked out wlassistant, I have been told that it plays way nicer with ndiswrapper than network-manager. let me know. also, is a gui a must for ya? just uninstall network-manager and just use the command line to find hot spots etc etc.

---

### Post by Erl1d on 2007-05-07
I'm having the same problem on a Lenovo N100. It worked perfectly on edgy, but after upgrading to feisty this problem appeared. Like Maxsilver wrote this problem is only when using networkmanager. The N100 uses a Broadcom BCM4310 wireless adapter. I have also tried a fresh install from the feisty cd, but this gives med the same result.

---

### Post by dirtytoyota4x4 on 2007-07-19
I also have a Lenovo 3000 N100 and seem to be having the same problem with network manager not working with ndswrapper. The only way I get internet is to type dhclient into the terminal and network manager only shows me what networks are available but wont connect to them.

---

### Post by learner on 2007-07-28
this thread seems to help: [http://ubuntuforums.org/showthread.php?t=493958](http://ubuntuforums.org/showthread.php?t=493958)

---

### Post by kevdog on 2007-07-28
Might want to give wicd a try if you want a "roaming mode" gui.  The CVS,beta, or developmental version is better than the stable version:
[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by DuckMan on 2007-07-31
wicd is awesome, works perfect

---

