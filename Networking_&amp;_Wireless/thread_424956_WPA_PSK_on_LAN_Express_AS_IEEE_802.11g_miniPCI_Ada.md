---
title: "WPA/ PSK on LAN Express AS IEEE 802.11g miniPCI Adapter"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by mskadu on 2007-04-27
Hi,

I recently helped someone install and start using Fiesty on a old laptop. That particular person has the above wireless card (as shown in Windows). I cant seem to get that laptop to connect to a Wifi adapter thats got WPA/PSK auth with TKIP encryption.

Is this not supported? :confused:

---

### Post by spd106 on 2007-04-29
Hi,
I do not recognise the name so it makes diagnosis rather difficult. Could you please open a terminal/cli and run these commands, then post the results here.
```
lspci
```
```
iwconfig -a
```
```
sudo lshw -class network
```

Thanks

---

### Post by mskadu on 2007-04-29
I have managed to do this now using wpa supplicant. For more details, see:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-0ea8cdec8956fd98e68d5c887976b6bc331d95cb](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#head-0ea8cdec8956fd98e68d5c887976b6bc331d95cb)

:popcorn:

thanks for your help though. If anyone else is interested, please drop a reply here and i can lay down the steps I went through. Although if you follow the link above you should be able to do it on your own.

One note, in the network-admin applet (on Fiesty Fawn), my wireless connection now has "Roaming Mode" box checked. This seems to have disabled all other boxed (ESSID, Password, etc). Any idea what this means?

---

### Post by spd106 on 2007-04-29
I'm glad you have got it working. If possible could you follow the supported wifi cards sticky and add your card to the list.

Roaming mode will allow you to quickly connect to networks that you have connected to in the past without having to re-enter all of the details. So it's quite handy if you frequently change networks (home/work/uni etc).

---

### Post by mskadu on 2007-04-30
Sticky?

> **spd106 said:**
> If possible could you follow the supported wifi cards sticky and add your card to the list.

---

### Post by spd106 on 2007-04-30
The top four threads in the Networking & Wireless subforum are sticky threads that don't move down the list, these offer advise and answers to commonly asked questions. 

Here's a link [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by yj09 on 2007-06-19
I got wireless problem. can somebody help me to solve my problem. I run feisty 2.6.20.16 latest kernel.

sudo lshw -class network
  *-network:0 DISABLED
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5
 latency=64 link=no multicast=yes
       resources: iomemory:d000a000-d000afff irq:10
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 00
       serial: 00:0b:cd:a9:4c:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii fibre 10bt 10b
t-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driververs
ion=2.1 duplex=full ip=192.168.0.143 latency=90 link=yes maxlatency=52 mingnt=11
 multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:2400-24ff iomemory:d0008000-d0008fff irq:10

---

### Post by weighedpolux on 2007-12-09
Hi can you list the steps to get the wirless card working?
Thanx

---

