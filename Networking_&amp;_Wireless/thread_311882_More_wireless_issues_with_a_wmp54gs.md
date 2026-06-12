---
title: "More wireless issues with a wmp54gs"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Sauwan on 2006-12-03
Alright, sorry about starting yet another brand new thread on this. I have sifted through all the other threads and can't find any with my same wireless card (the linksys wmp54gs), and because it seems to be a card specific issue, I thought if I could resolve it here it would be of use to others.

I initially followed the details for the usb version in the sticky. Although I used synaptic to install ndiswrapper, it seems to have worked. I  I seem to have most everything up, but am not getting any results. Here are the results from a few commands:

```
sudo ndiswrapper -l
Password:
Installed drivers:
wmp54gs         driver installed, hardware present 
wmp54gsa                driver installed, hardware present 

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 01
       serial: 00:50:8d:91:2c:26
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r1000 ip=192.168.1.105 multicast=yes
       resources: ioport:ee00-eeff iomemory:fdeff000-fdefffff irq:177
  *-network
       description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth1
       version: 01
       serial: 00:50:8d:91:2c:27
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r1000 multicast=yes
       resources: ioport:de00-deff iomemory:fdcff000-fdcfffff irq:169
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@05:05.0
       logical name: eth2
       version: 02
       serial: 00:16:b6:99:bf:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fd9fc000-fd9fdfff irq:58

```

Here's what my network settings look like:
[[img=http://img129.imagevenue.com/loc335/th_75586_wireless_122_335lo.jpg]](http://img129.imagevenue.com/img.php?image=75586_wireless_122_335lo.jpg)
(I enabled the wireless after doing the above commands...)


And this:
[[img=http://img170.imagevenue.com/loc457/th_75777__122_457lo.]](http://img170.imagevenue.com/img.php?loc=loc457&image=75777__122_457lo.)

I also installed the wifi radar, but it never picks up any networks in range. (Normally we have about 10)

What am I doing wrong here? I feel like I'm really close but just can't quite pull it together. Thanks a lot.

---

