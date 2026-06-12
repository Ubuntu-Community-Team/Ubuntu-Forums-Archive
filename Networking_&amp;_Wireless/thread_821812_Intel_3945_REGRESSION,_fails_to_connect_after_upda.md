---
title: "Intel 3945 REGRESSION, fails to connect after updates around June 6"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by g3brownsc on 2008-06-07
Hello all; I'm unofficially and tentatively reporting that intel 3945 has broken after an update, one I downloaded around June 6, possibly the 5th. 
I had it working for a while, since i did a fix after hardy came out.
I've re-installed hardy and done the following 

sudo apt-get install linux-backports-modules-hardy
sudo apt-get install linux-backports-modules-hardy-generic

which re-activated the light. 

I can see wireless networks, but fail to connect every time. My laptop is a brick without wireless, and I need to fix this as quickly as possible. Anyone with a Thinkpad R61 or the Intel 3945 wireless card, please help. I don't have access to a linux guru, and I need to get my laptop working for this last week of school. Thanks in advance.

---

### Post by braveerudite on 2008-06-07
> **g3brownsc said:**
> Hello all; I'm unofficially and tentatively reporting that intel 3945 has broken after an update, one I downloaded around June 6, possibly the 5th. 
I had it working for a while, since i did a fix after hardy came out.
I've re-installed hardy and done the following 

sudo apt-get install linux-backports-modules-hardy
sudo apt-get install linux-backports-modules-hardy-generic

which re-activated the light. 

I can see wireless networks, but fail to connect every time. My laptop is a brick without wireless, and I need to fix this as quickly as possible. Anyone with a Thinkpad R61 or the Intel 3945 wireless card, please help. I don't have access to a linux guru, and I need to get my laptop working for this last week of school. Thanks in advance.

I have same issues.. I can see wireless networks, but fail to connect every time.

---

### Post by g3brownsc on 2008-06-07
I don't get it. 3945 is a really common wireless chipset, how can we have such gigantic snafus on an LTS release? 

I tried re-installing everything wireless. It may be a problem with a kernel upgrade, that seems to be what broke it the first time, during the upgrade from feisty to hardy. 

That said, I don't know enough about this to make an educated guess. We could really use the help of someone who borderline knows what they're doing, or, failing that, more people with the same problem.

---

### Post by chili555 on 2008-06-07
I guess I qualify: I borderline know what I'm doing and I have a working-perfectly 3945ABG on Hardy with all updates. 

First of all, I'm not sure 'we,' in the sense of Ubuntu, have a problem. *modinfo iwl3945* tells us the author of the module is:> author:         Copyright(c) 2003-2007 Intel CorporationNot much the Ubuntu developers can do, unless they want to get into writing device drivers. As far as I know, *no* wireless drivers are actually written by the Ubuntu developers, just as they don't write Gnome, KDE, Open Office, Python, etc.

Second, do you have a Network Manager issue or an iwl3945 issue? Can you disable Roaming and connect manually easily?```
sudo iwconfig wlan0 essid <ur_essid>
sudo iwconfig wlan0 key <any_encryption_here>
sudo dhclient wlan0
```

Finally, may I please see:```
iwconfig wlan0
sudo iwlist wlan0 scan
```Thanks.

---

### Post by robfantini on 2008-06-07
I have the same problem,  Until it is fixed am using wifi-radar .  

sudo aptitude install wifi-radar

access it at Applications > Internet > Wifi-radar

it stores info at /etc/wifi-radar.conf

here is an example config:
[FIOS-536]
prescript =
use_wpa = no
postscript =
mode = auto
key = xxxxxxxxxx
use_dhcp = yes
security =
channel = auto



Description: graphical utility for managing Wi-Fi profiles
 It enables you to scan for available networks and create profiles for your preferred networks. At boot time, running Wi-Fi
 Radar will automatically scan for an available preferred network and connect to it. You can drag and drop your preferred
 networks to arrange the profile priority.

---

