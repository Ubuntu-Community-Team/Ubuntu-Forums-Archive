---
title: "Wireless Configuration Issue"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by gauravkumar on 2011-03-18
Hi All,
I installed fresh copy of Ubuntu 10.10 in my system.
I am trying to configure my wifi, but I cannot get the interface for any such device. But everytime below mentioned messages are reflected.

gaurav@gaurav-Studio-1558:~$ sudo lshw -C network
[sudo] password for gaurav: 
  *-network DISABLED      
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:60:6e:0b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:19:89:0d
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:46 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff memory:f0420000-f043ffff
gaurav@gaurav-Studio-1558:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

ppp0      no wireless extensions.

gaurav@gaurav-Studio-1558:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
gaurav@gaurav-Studio-1558:~$

---

### Post by seawolf167 on 2011-03-18
Please physically plug your computer into your wireless device and do the following:

to show your route to the default gateway (since it is physically plugged in and providing your WAN/LAN access)

```
route
```

look for the gateway number (usually 192.168.x.x) for the row that starts with the word "default"

then open Firefox (or any browser) and type the address into the address bar, i.e.

```
http://192.168.x.x
```

hit enter, enter your username/password, then you will be able to setup your wireless router (SSID, passphrase, etc.)

once you have it setup, you can unplug your computer and connect to your WiFi

---

### Post by gauravkumar on 2011-03-18
I have a laptop I'm working on. And I think it already contains a wifi card. Please suggest how can I track this and how can I set it to monitor mode to work with aircrack commands.

---

### Post by wep940 on 2011-03-19
To clarify something so we can address the problem - are you talking about setting up a router, or are you talking about setting up a wireless connection on your laptop?
 
If you are trying to set up a wireless connection on your laptop:
 
[LIST]
[*]the output shows the wireless is using the wl0 driver
[*]the output shows the wireless as disabled:
[LIST]
[*]does your laptop have a on/off button for wireless? If so, try toggling it, but be aware the some people have to actually boot Windows, toggle it on there, then come back to Ubuntu and go from there (should be good "forever" as as nobody toggles the button).
[/LIST]
[*]right-click on the network manager icon: Is "Enable Wireless" checked? If not,
[LIST]
[*]check it to enable it (if it doesn't show or is grayed out, reply back here)
[/LIST]
[*]left-click on the network manager icon: do any wireless networks show?
[*]does the router broadcast the network name or is it a "hidden" network? If
[LIST]
[*]it is hidden you must use the "Connect to hidden network" option in network manager.
[/LIST]
[*]It's also possible one of the other Broadcom drivers either needs to be blacklisted or is blacklisted when it shouldn't be
[/LIST]

---

