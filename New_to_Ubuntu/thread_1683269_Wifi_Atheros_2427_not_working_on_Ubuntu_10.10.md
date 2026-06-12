---
title: "Wifi Atheros 2427 not working on Ubuntu 10.10"
date: 2011-02-07
forum: New to Ubuntu
---

### Post by Antwerpen on 2011-02-07
Hello,
I have bought the following netbook:

ASUS EeePC1001PX Atom N450 1GB*DDR2 160GB WiFi XpHome 10.2" 
Asus model EPC1001P, Intel® Atom N450 @ 1.66GHz, 1GB DDR2, etc.

Of course, I removed the slow xp home edition, and I installed an ubuntu 10.10 based distro (DDUbuntu 2.0) with lxde as windows manager.

Everything seems to work fine, except for the wireless. My netbook has an Atheros 2427 wifi card. When I list the pci I see also the Atheros 2427 (ath9k) drivers.

If I try to connect to the wireless through wicd it does the scan for the wifi(s) networks, it finds them and lists them. Then I try to connect, and the dialog tell that the interface is going up, and then "getting ip address", or something like that. But then the ip is never obtained and the error "Unable to get ip address" appears, likely due to a timeout.

Then I tried to avoid graphical interface and I used iwconfig and tried to scan on my interface wlan0. It listed the wireless networks properly, most of them unsecured. But then I tried to use

-> iwconfig wlan0 channel numberOfTheChannel essid essidOfANetwork mode Managed ap apAddress

, and then restart the network interfaces (/etc/init.d/network restart) but it was not working.

What is the problem, how can i solve it in an elegant way?
Ps: I would like to avoid Ndiswrapper :)

---

### Post by Pevichaey5 on 2011-02-07
I have a 1005HA, which has an Atheros chipset wireless card as well and mine works fine.

I am running BackTrack 4 on mine however I believe this is based on Ubuntu (8.04?).  Connecting to a WPA enabled wireless network is a bit different and I use wpa_supplicant to connect to it, then I need to obtain an IP address which I can set manually or using dhclient.

```
/etc/init.d/wicd start
```
Then start the wicd GUI and just select your network from the list and set the encryption and key as appropriate

---

### Post by Antwerpen on 2011-02-07
Actually It's what I did and it's not workin' at all...

---

### Post by Aero_Zeppelin on 2011-02-07
Hi,I have an eee1005px which has an Atheros AR2427 wireless adapter and it works out of the box.

---

### Post by Antwerpen on 2011-02-07
> **Aero_Zeppelin said:**
> Hi,I have an eee1005px which has an Atheros AR2427 wireless adapter and it works out of the box.

Well, mine does not... any suggestion? :confused:

---

### Post by dareni on 2011-04-28
Aero_Zepplin what version are you running? I have a 1001px with the AR2427 and have had no luck with FreeBSD current and Fedora 14 and 15 alpha. I am able to scan access points but always get a time out on the attempt to associate.

---

### Post by gandaran on 2011-04-28
> **dareni said:**
> Aero_Zepplin what version are you running? I have a 1001px with the AR2427 and have had no luck with FreeBSD current and Fedora 14 and 15 alpha. I am able to scan access points but always get a time out on the attempt to associate.
hi
there is also the possibility the problem is the router and not your computer, check and ensure that DCHP server is enabled in the router configurations.

---

