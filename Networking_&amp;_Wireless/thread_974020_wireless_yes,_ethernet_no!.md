---
title: "wireless yes, ethernet no!"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by ziofil on 2008-11-07
Hi everybody
it's one hour that i surf through the forum to find a solution to my issue, but it seems that i need to start a new thread...

I have a benq laptop running xubuntu 8.10, it can connect to the wireless network (i'm using it to write you) but it can't with the ethernet cable.

the output of lshw -C network is:

```
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth0
       version: 05
       serial: 00:0e:35:8b:f7:d9
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.16.72 latency=128 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 83
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
```

so I have a single device (eth0) which is the wireless network device, as it shows also in iwconfig and ifconfig.
The output of lspci -knn (the section regarding the ethernet controller) is:
```
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
	Kernel modules: eepro100, e100
```

I don't really know what to do... A couple of hours ago, before upgrading to intrepid everything was ok.
Anyone had the same problem? Did you find a workaround? I can't play with /etc/network/interfaces as long as the interface doesn't exist right?
Thank you in advance

---

### Post by ziofil on 2008-11-07
I solved the problem, although I don't know why it worked: I did a ```
sudo update-rc.d -f NetworkManager remove

```
and rebooted
then I just had to bring the interface up and play with dhclient.

---

