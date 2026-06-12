---
title: "ndiswrapper + changing mac"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by antek on 2007-03-07
Hello,

I'm using windows' bcmwl5.sys driver via ndiswrapper for my Broadcom BCM4318 wireless card, and I can't make it to change it's MAC address. I am trying to do it by ifconfig eth1 hw ether <newmac>, but it's not displaying anything at all, and the mac stays unchanged. When there's internet connection active and I try to change the MAC using this method, the connection resets and wpa_supplicant displays some messages that it tries to reconnect to the network. I also tried to modify the configuration files of ndiswrapper. I am getting the name of conf file from dmesg:
```
[20741.126000] wlan0: ethernet device <mac> using NDIS driver: bcmwl5, version: 0x40a2800, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
```
and changing this line in the conf file:
```
mac_address|00:00:12:5A:C0:4F
```
but it still has old mac, in dmesg and in ifconfig. Any more options?

---

