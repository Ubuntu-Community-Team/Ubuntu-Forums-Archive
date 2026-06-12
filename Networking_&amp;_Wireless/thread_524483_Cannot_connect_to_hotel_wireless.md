---
title: "Cannot connect to hotel wireless"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by mastergunner on 2007-08-13
Guys I am having a terrible time with this. I can connect to every other wireless service except the hotel I am staying and I will be here for a while. I need the internet!!!! I am using kubuntu 7.04. I have a HP pavilion laptop. Network manager sees the service and when I try to connect it gets to 57% (IP Configuration started) and then does nothing and times out. I am using the hotels guest computer right now so what do I need to do. I am a noob so instructions should be very thorough. Thanks for everyones help and contribution on this forum. It has helped me tremendously.

---

### Post by moore.bryan on 2007-08-13
*are you sure your hotel doesn't charge extra for internet access?  i know courtyards do...*

---

### Post by mastergunner on 2007-08-13
No it is free at the Crown Plaza I am staying at.

---

### Post by moore.bryan on 2007-08-13
*are you using network-manager or wicd?*

---

### Post by mastergunner on 2007-08-14
network manager. what is wicd?

---

### Post by moore.bryan on 2007-08-14
*[wicd]("http://wicd.sourceforge.net/") is an alternative "network manager" which solves a lot of problems for a lot of people (me included)...*

---

### Post by mastergunner on 2007-08-14
Well unfortunately I cannot download it cause no internet access LOL. Any other ideas?

---

### Post by bjarneh on 2007-08-14
the hotel uses WEP or WPA encryption? you could try to manually configure it, just killing that NetworkManager (if it's WEP it should be done in a flash) 

$ sudo ifdown eth1
$ sudo iwconfig eth1 mode managed essid FancyHotel key restricted \
012345abcde

$ sudo ifup eth1

(if the ESSID is called FancyHotel, and their encryption key is 0123...)

you will have to stuff these lines into your /etc/network/interfaces

auto eth1
iface eth1 inet dhcp

---

### Post by mastergunner on 2007-08-14
It is not encrypted. ETH1 on my computer is LAN. My wireless is wlan0. Through network manager it sees stayonline which is what the hotel is using but it wont connect. Oh I am so lost.

---

### Post by mastergunner on 2007-08-17
Can anyone else help me. I am using a Netgear WG511 v1 card.

---

### Post by wieman01 on 2007-08-17
> **mastergunner said:**
> Can anyone else help me. I am using a Netgear WG511 v1 card.
Have you - at some point - set a static IP and disabled DHCP on your PC? You can check under "Manual Configuration..." in Network Manager.

---

### Post by kevdog on 2007-08-17
This should be too hard

Your wireless interface is wlan0 (at least that what you are telling me)

So try the following (some of this is overkill)  Notice 2nd line from the bottom.  Choose one option, not both!!

sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo ifconfig wlan0 essid "FancyHotel"
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key <HEXKEY> or <s:ASCIIKEY>
sudo dhclient wlan0

---

