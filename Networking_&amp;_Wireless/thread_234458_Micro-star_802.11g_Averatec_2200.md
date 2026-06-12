---
title: "Micro-star 802.11g Averatec 2200"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by nvbauer on 2006-08-11
hello all, 

Just bought a Averatec 2200. All works well except for the integrated wireless card (big shocker there). It is a Micro-star 802.11g card (I think that's the same as the mobo manufacurer MSI). Has anyone had anyluck getting it to work on theirs. 


Thanks,

Norm

---

### Post by GavinX on 2006-08-11
Do you know the chipset of the wireless card........ although the card may manufactured by Microstar, the chipset may be something different. Give that info then more help will come.

---

### Post by GavinX on 2006-08-11
OK......... I found some info....... your card is manufactured by MSI but uses the rt2500 driver........ according to the Ubuntu Wiki, it should work out of the box on Dapper.

Edit: Check this page, it should help [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

---

### Post by nvbauer on 2006-08-11
Thanks, but it does not work out of the box. I did modprobe on rt2500 & rt2400 but that does not work either. Also tried orinoc_cs (just for giggles)

---

### Post by GavinX on 2006-08-11
Do you have any kind of encryption or firewall set up on your network?

---

### Post by GavinX on 2006-08-11
what does iwconfig give?

---

### Post by nvbauer on 2006-08-11
> **GavinX said:**
> what does iwconfig give?

norm@darkstar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


I am still trying to find out the exact chipset this baby uses.

---

### Post by GavinX on 2006-08-11
do the following
1. run:

sudo gedit /etc/network/interfaces

2. In that file add these lines:

auto wlan0
iface wlan0 inet dhcp



iface ra0 inet dhcp
wireless-essid **linksys**

auto ra0
 
[B](make sure you substitute "linksys" with your essid)
[/B]
4. Go to the the NetworkMonitorand select ra0 and click on activate

Let me know what happens

---

