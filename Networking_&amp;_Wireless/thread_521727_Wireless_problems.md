---
title: "Wireless problems"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by Warpedflash on 2007-08-09
For about a week i have been getting the following message on logging into ubuntu,

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

and i was just putting up with it... and its not high on my list to correct it but if anybody has an answer thanks.


Now the main problem is yesterday i upgraded to the gusty kernel and since then i cannot connect to wireless networks, if i try to conect to an unsecured network it just wont.. if i try and connect to a secure network it just crashes and completely locks up  meaning i have to old power down. 

if you can help thanks :)


edit: my laptop also appears to now be called dplay.so.1/u rather than ubuntu_laptop




further edit : i hope this info helps

rowan@dplay:~$ sudo lshw -C network
  *-network               
       description: GCS2000
       product: Gold II
       vendor: Grey Cell
       physical id: 0
       version: 1
       slot: Socket 1
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:78:68:b0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.71 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:e8120000-e8120fff ioport:1800-183f iomemory:e8100000-e811ffff irq:11
  *-network
       description: Wireless interface
       product: Ralink RT2600 802.11 MIMO
       vendor: RaLink
       physical id: 1
       bus info: pci@02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:17:3f:8b:b0:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:24000000-24007fff irq:11
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth1
       serial: 00:47:43:35:27:14
       capabilities: ethernet physical
       configuration: broadcast=yes driver=pcnet_cs multicast=yes
rowan@dplay:~$ cat /etc/network/interfaces


rowan@dplay:~$ sudo cat /etc/network/interfaces


rowan@dplay:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rowan@dplay:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     No scan results

---

### Post by buntunub on 2007-08-09
Looks to me like your going to have to recompile your wireless settings all over from scratch. Things like this happen when you upgrade kernels. Id be surprised if your video drivers didnt get hosed up too.

---

### Post by Warpedflash on 2007-08-10
how would i go about re-compiling my wireless settings?
my vid drivers should be fine i am on an old laptop so its all onboard.


i have tried to install the new drivers from the belkin with ndiswrapper and amazingly... it crashes out and now i cant even open the ndiswrapper gui... and now with the wireless card in i cant open the normal network control pannel either

---

### Post by Warpedflash on 2007-08-10
I still need help... sorry to bump up but i need my wireless..

---

### Post by Warpedflash on 2007-08-11
> **Warpedflash said:**
> I still need help... sorry to bump up but i need my wireless..

Bump... bump...

---

### Post by Warpedflash on 2007-08-12
Any1 help ?

---

