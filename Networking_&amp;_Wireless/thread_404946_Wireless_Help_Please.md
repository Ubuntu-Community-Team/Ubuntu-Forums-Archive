---
title: "Wireless Help Please?"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by NaiNebel on 2007-04-09
I have a Broadcom 4306 wireless LAN thing in my HP Pavilion zv5000. Unfortunately, it doesn't seem like Ubuntu likes it. After several hours with a friend working on it, we got the drivers to work and all. Unfortunately, the thing won't connect to my wireless network. Any help would be appreciated.

---

### Post by sirbats on 2007-04-09
> **NaiNebel said:**
> I have a Broadcom 4306 wireless LAN thing in my HP Pavilion zv5000. Unfortunately, it doesn't seem like Ubuntu likes it. After several hours with a friend working on it, we got the drivers to work and all. Unfortunately, the thing won't connect to my wireless network. Any help would be appreciated.

Hi NaiNebel,
if u wish to ask for help for hardware i.e wireless adapter; pls post ur result for $lspci command and copy at the wireless part.

example :
```

$lspci
02:01.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

on your case pls inform ; how is the router set-up; u r using wep-key static IP or dhcp.

thanks
sir Bats

---

### Post by NaiNebel on 2007-04-09
The reply to the command is thus:

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

I'm using a wireless network modem with SSID broadcast (2WIRE900) and password/encryption removed for the time being.

I'm able to manually put it in, and a iwconfig shows that it's set up correctly on eth1. However, it can't seem to connect.

On another note, I'm also a Linux newbie (like, 2 days), so I'll need explanations of anything that's not outright understandable.

---

### Post by sirbats on 2007-04-09
> **NaiNebel said:**
> The reply to the command is thus:

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless Lan Controller (rev 03)

I'm using a wireless network modem with SSID broadcast (2WIRE900) and password/encryption removed for the time being.

I'm able to manually put it in, and a iwconfig shows that it's set up correctly on eth1. However, it can't seem to connect.

On another note, I'm also a Linux newbie (like, 2 days), so I'll need explanations of anything that's not outright understandable.

Please set-up your router to enable dhcp ; remove encryption. 
try this :

```

$ sudo dhclient eth1

```

In my feisty I have to install dclient and remove dhc3 via synaptic.

thanks

---

### Post by NaiNebel on 2007-04-09
Response:

> Listening on LPF/eth1/[mac address]
Sending on LPF/eth1/[mac address]
Sending on Socket/Fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - Sleeping

---

### Post by sirbats on 2007-04-10
Hi NaiNebel,

Please check wether your router set-up is dhcp enable, network is up. My experience with feisty. I have to un-install gnome network manager, uninstall dhcp3-client (installed by default during installation) . 

Please ensure the package : dhcp-client, dhcp3-common and avahi-autoipd : installed. You can check on the synaptic.

I faced the same problem, after remove gnome-network-manager and dhcp3-client and install dhcp-client, dhcp3-common and avahi-autoipd : I got  this :

```

sts@opotumon:~$ sudo dhclient ra1
Password:
Internet Software Consortium DHCP Client 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit http://www.isc.org/dhcp-contrib.html

Listening on LPF/ra1/00:16:b6:99:73:c9
Sending on   LPF/ra1/00:16:b6:99:73:c9
Sending on   Socket/fallback/fallback-net
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 3
receive_packet failed on ra1: Network is down
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra1 to 255.255.255.255 port 67 interval 19
DHCPOFFER from 192.168.1.234
DHCPREQUEST on ra1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.234
bound to 192.168.1.109 -- renewal in 43200 seconds.
sts@opotumon:~$ 

```

Ref to your out-put: you did not get mac address: pls check wether you can give input manually.

best regard

---

### Post by josephus on 2007-04-10
Are we sure that this is a problem with dhcp?  It seems quite possible that the card is not even associated with the access-point.

Can you give the output to:

```
ifconfig
iwconfig
iwlist scan
lshw -class Network
```

---

### Post by NaiNebel on 2007-04-10
I'll have to download the package on another computer. Part of my issue is that I can't get any packages right now. My ethernet seems to have broken down and I'm not sure why.

---

### Post by NaiNebel on 2007-04-10
ifconfig:
> Eth1 Link Encap: Ethernet  HWaddr 00:90:4B:9D:B4:62
inet addr:192.168.0.66 Bcast: 192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::290:4bff:fe9d:b462/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric: 1
Rx packets: 17 Errors:0 dropped:0 Overruns:0 frame:0
Tx packets:15 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
Rx bytes: 2478 (2.4 KiB) TX bytes: 1474 (1.4 KiB)
Interrupt:217 Memory:e8100000-e8102000

iwconfig:
> IEEE 802.11g ESSID:off/any
Mode:Managed Frequency: 2.462 GHz Acces Point: Not-Associated
Bit Rate: 54 Mb/s Tx-power: 25 dBm
RTS thr:2347 B Fragment thr: 2346 B
Power Management:Off
Link quality:0 Signal Level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt: 0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

iwlist scan isn't showing anything on eth1, though usually it shows my network.

lsh -class Network:
> *-network:1
Description: Wireless Interface
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id:2
bus info: pci@02:02.0
logical name:eth1
version: 03
serial: 00:90:4b:9d:b4:62
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper ip=192.168.0.66 multicast=yes wireless=IEEE 802.11g
resources: iomemory:e8100000-i8101fff irq:217

---

### Post by josephus on 2007-04-10
You are not associated with the router.  I don't think your ndiswrapper is being loaded up correctly.  Did you remember to blacklist bcm43xx driver?

[http://ubuntuforums.org/showthread.php?t=340689&highlight=bcm4306+ndiswrapper](http://ubuntuforums.org/showthread.php?t=340689&highlight=bcm4306+ndiswrapper)

edit: you can also use dmesg to see if there are any errors related to the wireless card

---

