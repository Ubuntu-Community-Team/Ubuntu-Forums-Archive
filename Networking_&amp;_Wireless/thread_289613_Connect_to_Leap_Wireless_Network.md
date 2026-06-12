---
title: "Connect to Leap Wireless Network"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by jjhart on 2006-10-31
At my school, they use a LEAP wireless network with a hidden SSID.  I know the SSID, so that isn't the problem, I have to use a user name and password under LEAP authentication and there isn't an option for that in Network manager.  Is there any way to connect to a LEAP network?  I just installed Edgy on a NC6000 laptop.

---

### Post by wieman01 on 2006-10-31
I have to admit I have not done it myself, either, but I have got WPA2 (AES) running so perhaps that closer than you are now. Let's give it a try then if you don't mind:

**1.** Open "interfaces" (make a safety copy of your file before you go ahead):
> sudo gedit /etc/network/interfaces
**2.** I don't know what wireless interface your using, but I assume it is "eth1" with DHCP. Now paste this:
> auto lo
iface lo inet loopback

auto [COLOR="Blue"]eth1[/COLOR]
iface [COLOR="Blue"]eth1[/COLOR] inet dhcp
wpa-driver [COLOR="Blue"]wext[/COLOR]
wpa-conf managed
wpa-ssid [COLOR="Red"]your_essid[/COLOR]
[COLOR="SeaGreen"]wpa-ap-scan 2[/COLOR]
wpa-eap LEAP
wpa-key-mgmt IEEE8021X
wpa-identity [COLOR="Red"]your_user_name[/COLOR]
wpa-password [COLOR="Red"]your_password[/COLOR]
[COLOR="Blue"][It's likely that **"wext"** is not the right driver for you. Please let me know what wireless card you're using & the chipset.][/COLOR]

**3.** Then restart the network:
> sudo /etc/init.d/networking restart
Please post the output if possible.

**4.** This is for you to read... Good documentation: [http://en.wikipedia.org/wiki/Lightweight_Extensible_Authentication_Protocol]("http://en.wikipedia.org/wiki/Lightweight_Extensible_Authentication_Protocol")

**5.** And please tell your network administrator that WEP based wireless networks are NOT secure... WPA2/EAP are what's considered up to standard.

_**EDIT 1:**_
Please paste your current version of "/etc/network/interfaces" so that we understand what your setup is.

_**EDIT 2:**_
"wpa-ap-scan 2" stands for "hidden" ESSID.

---

### Post by jjhart on 2006-10-31
I can't check that right now because I am not at school, but what about when I have to switch to another type of network, do I have to go in and edit it again?  I connect at school with one type, at home with another type, at my in-laws with another encryption and at work with another.  I might do all four networks in one day.  I can't be going in and editing the network setup each time.  I need to be able to click on the Network manager and select a certain profile, say "home" or "work" or "inlaws" and have it just connect with all of my settings saved.  Is that at all possible

---

### Post by wieman01 on 2006-10-31
LEAP is a proprietary solution (Cisco) & I am not away of any graphical wireless configuration tool (e.g. NetworkManager, Wifi-Radar) supporting it.

Nonetheless, check out gnome-network-manager/network-manager & wifi-radar. Perhaps those are options for you. But I doubt it.

---

### Post by jjhart on 2006-11-01
I have tried network manager, I even tried the network manger cvs version which is in the developmental stage to support LEAP but it doesn't seem to fully work on my school's network.  I will try to get help from the guys that know a little bit more about the cvs version to see if they can help.

---

### Post by wieman01 on 2006-11-01
Try that. As a fallback you can configure LEAP yourself. But like I have said, it's proprietary & fairly outdated... Therefore support is unlikely. Perhaps NetworkManager is an option soon.

---

### Post by wieman01 on 2006-11-01
Just found this Howto on LEAP & NetworkManager. Perhaps it helps:

[http://www.ubuntuforums.org/showthread.php?t=235655]("http://www.ubuntuforums.org/showthread.php?t=235655")

---

