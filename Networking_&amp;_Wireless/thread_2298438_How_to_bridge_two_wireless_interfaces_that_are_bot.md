---
title: "How to bridge two wireless interfaces that are both on the same computer ?"
date: 2015-10-11
forum: Networking &amp; Wireless
---

### Post by sean106 on 2015-10-11
Ubuntu 14.04

Basically I am trying to accomplish the following setup -

wireless internet ---> wlan0 of Ubuntu computer "bridged to" wlan1 of same Ubuntu computer ---> device with wifi

The reason for this setup is that the wireless internet is a WPA2  Enterprise network which my device with wifi cannot connect to. (The  device with wifi also cannot connect to peer-to-peer networks or ad-hoc  networks.) Also, the wireless internet source has no whitelist /  blacklist and therefore there is no issue with it seeing the device's  MAC address (if necessary), and no issue with it assigning an IP address  to the device (if necessary). It is the device that has an issue with  WPA2 Enterprise authentication.

[**EDIT** - As the device cannot successfully authenticate,  the wireless internet source is NOT likely to assign an IP address to  the device, and also likely to take issue with seeing the device's MAC  address.]

wlan0 is an Intel wireless chipset / interface which  cannot be set to either access point mode or master mode, and therefore  is used to connect to the WPA2 Enterprise internet source.
wlan1 is to be set to access point mode.
  Obviously, the "bridge" between wlan0 and wlan1 is not meant to be wireless, as both are on the same computer.
  
[LIST=1]
[*]I believe brctl cannot bridge a wireless interface (wlan0) to another wireless interface (wlan1). Is this correct? 
[*]If brctl cannot be used, can I still use hostapd? 
[*]If brctl cannot be used, what should I be looking for to accomplish the setup described above? 
[*]Would any of the following be a part of the solution to my problem - (a) dnsmasq to serve DHCP (b) hostapd (c) static IP address (for wlan1 ???) (for the device connected to wlan1 ??) (d) NAT (Network Address Translation) (e) iptables (f) IP Masquerade (g) sudo iw set dev wlan0 4addr on (h) WDS (wireless distribution system) (i) IP forwarding ? 
[/LIST]

---

### Post by TheFu on 2015-10-12
I don't know if this is possible, but perhaps you want to make the system a "router" using each wifi interface for a different subnet? There are lots of how-to guides to make a linux machine into a router. I know people to it with 1 wifi and 1 ethernet interface all the time. Don't know about 2 wifi, however.

Just an idea.

---

### Post by sean106 on 2015-10-16
[Solved]
I used iptables instead of brctl. Issue closed.

---

