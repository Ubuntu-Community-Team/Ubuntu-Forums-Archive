---
title: "Can't connect to my wireless network"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by slither on 2007-07-12
Hello all.
I just installed Ubuntu 7.04 on my acer laptop which came with an atheros wireless card. I have madwifi installed and as far as I can see in the network manager it detects all the available wireless networks. The problem is that it won't connect to any of them no matter how much I try. It just prompts for a network key and once I type it in , it tries to connect for a few seconds then switches back to the wired connection. I am sure the network key is correct, I have typed it in dozens of times. I read some of the older threads in this forum and followed the instructions but still no luck. 
I appreciate any help from you guys.
Regards

---

### Post by Azoix on 2007-07-12
[B][COLOR="Blue"]Try adding the WEP key in terminal , with root permissions ,
command : if your wireless interface is wlan0 if its wlan1 , use this in the command.

iwconfig wlan0 key open YOUR WEP KEY HERE 
iwconfig wlan0 essid YOUR NETWORK ID HERE
iwconfig
iwconfig
iwconfig wlan0 commit
[/COLOR][/B]

[COLOR="Red"]Hope this works for you.[/COLOR]

---

### Post by slither on 2007-07-12
Thank you for your fast reply.
I tried that but still no luck :confused:

---

### Post by Paris Heng on 2007-07-12
> **slither said:**
> Thank you for your fast reply.
I tried that but still no luck :confused:


Do you now still can't connect to the Internet?

---

### Post by kevdog on 2007-07-12
Are you trying to run a wired and wireless connection at the same time??? Although possible, its extremely difficult to configure, and in most cases not what people want to do, unless they are running a server or something.  In most cases, you need to bring down the wired interface, then bring up the wireless interface.  Vice versa if you want to reverse the process.

You need to give up more information
Posting your /etc/network/interfaces along with
lshw -C network
would help!

---

### Post by slither on 2007-07-12
Here is the content of /etc/network/interfaces:
[HTML]auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ppp0 inet ppp
provider ppp0[/HTML]

And this is the output of the  lshw -C network command:
[HTML]
  *-network:0             
       description: Wireless interface
       product: AR5005G 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@06:05.0
       logical name: wifi0
       version: 01
       serial: 00:14:a4:55:38:e9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (svn r2584) latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b0100000-b010ffff irq:17
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:eb:ec:9c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.160 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:3000-30ff iomemory:b0110000-b01100ff irq:23

[/HTML]
I tried shutting down the wired interface but I still couldn't connect to my wireless network.
Thank you so much for your help!

---

### Post by slither on 2007-07-13
anyone???

---

### Post by Azoix on 2007-07-13
[B][COLOR="Blue"]Open terminal and type 
sudo iwconfig and paste the result here please.[/COLOR][/B]

---

