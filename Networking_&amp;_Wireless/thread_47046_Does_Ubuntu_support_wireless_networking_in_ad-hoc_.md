---
title: "Does Ubuntu support wireless networking in ad-hoc mode?"
date: 2005-07-07
forum: Networking &amp; Wireless
---

### Post by john_walsh54 on 2005-07-07
Hi,
I have 2 laptops with the same wireless cards (DWL-G650). Both laptops are dual boot, with Windows XP and Ubuntu 5.04) I used ndiswrapper to install the windows driver for the cards and ndiswrapper reports > net5211 driver present, hardware present.
When I boot into Windows XP on my Thinkpad and boot into Ubuntu 5.04 on my Vaio, each laptop can see my network connection (PETER). However, when I boot into Ubuntu on both laptops there is no signal for the network. Does this mean a total Ubuntu network does not work in ad-hoc mode?
In System -->Administration -->Networking (network-admin) I have the following settings for the Thinkpad laptop which connects to the internet;
On the General Tab for host settings, hostname is ThinkPad and domain is PETER
On the DNS Tab, the DNS servers are  192.189.54.17 and 203.8.183.1 (I think these relate to the modem).
There are two connections available:
The Wireless Connection (ath0) have the following properties:
 Network name (ESSID): PETER
  WEP key: <empty>  [-X 
 Configuration: Static IP Address
 IP Address: 192.168.0.1
 Subnet Mask: 255.255.255.0
 Gateway Address: <empty>
The second connection is the Modem Connection (ppp0) but I don't think those details are required.
In System -->Administration -->Networking (network-admin) I have the following settings for the VAIO laptop;
On the General Tab for host settings, hostname is VAIO and domain is PETER
There is only one connection available for the VAIO (no modem):
The Wireless Connection (ath0) have the following properties:
 Network name (ESSID): PETER
 WEP key: <empty>  [-X 
 Configuration: Static IP Address
 IP Address: 192.168.0.2
 Subnet Mask: 255.255.255.0
 Gateway Address: 192.168.0.1
I tried using a DCHP configuration but when I ran ifconfig there were no IP addresses. Below is the route listing:
```
john@ThinkPad:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
acc10.hay.conne *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     0      0        0 ath0
default         acc10.hay.conne 0.0.0.0         UG    0      0        0 ppp0
```
Where does 192.168.0.0 come from? Could the fact that both wireless cards have the same connection name i.e. ath0 be causing the problem? If so, how do I change it as ubuntu generates this name?
With my firewall either on or off doesn't make a difference.
Thank you for your help

John

---

### Post by john_walsh54 on 2005-07-14
I found this [How to set up Ndiswrapper article](https://wiki.ubuntu.com/HowToSetUpNdiswrapper) which explains how to use windows drivers to get your wireless card working in Ubuntu.
I also found a document about [How to setup WIFI](https://wiki.ubuntu.com/WiFiHowto) which explains how to set my WIFI card to ad-hoc mode.```
sudo iwconfig ath0 mode ad-hoc
``` NOTE: ath0 is the device name for my card, yours may be different (wlan0).
As far as I can tell Ubuntu doesn't have a GUI which allows you to make these changes yet.
However, using these wireless tools did confirm that my wireless cards detect each other by identifying each others hardware ID as within range. Unfortunately, I still cannot get them to work, but I did notice something strange - the hardware ID in the wireless extension is different  to the hardware ID mapped to network connections. 

Could this bug be the cause of my problems?

---

