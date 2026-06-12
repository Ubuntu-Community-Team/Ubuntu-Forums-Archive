---
title: "Wireless not working"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2007-10-21
My laptop is a Clevo M66SE.
The wireless connection worked OK with Edgy and later with Feisty 7.04, but inexplicably stopped.

My Netgear DG 834G v3 wireless router works OK (other users have no dramas with it - using XP of course).
My wired connection works OK through the same router.

The manual tells me that it uses an internal USB wireless LAN module. When I invoke **lsusb** , I get:
Bus 005 Device 003: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 005 Device 002: ID 0402:5602 ALi Corp.

When I invoke **lshw -C network** I get:
*-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:90:f5:57:ba:bb 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 latency=32 maxlatency=8 mingnt=3 multicast=yes 
       resources: ioport:4800-48ff iomemory:cb400400-cb4004ff irq:21 
  *-network 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:15:af:12:7d:b7 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g  

With my limited knowledge, I'm assuming that because it does not specifically identify a driver associated with the wireless interface, it can no longer be seen by the system.

So, where in blazes did that little sucker go? And, what should I do next?

---

### Post by Buster95 on 2007-11-02
Don't know whether I'm providing too much information here but I don't seem to be able to associate a wireless driver with my RTL8187 internal usb wireless card. The following may give an idea of what I'm seeing. I've tried to highlight the relevant bits.

Can anyone guide me through this?
Thanks



dexter@dexim-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:90:f5:57:ba:bb 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.0.4 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes 
  [COLOR="Red"]*-network 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:15:af:12:7d:b7 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g [/COLOR]

dexter@dexim-laptop:~$ iwlist scanning 
lo        Interface doesn't support scanning. 
eth0      Interface doesn't support scanning. 
wmaster0  Interface doesn't support scanning. 
[COLOR="Red"]wlan0     No scan results[/COLOR] 

dexter@dexim-laptop:~$ sudo ifconfig wlan0 down 
[sudo] password for dexter: 

dexter@dexim-laptop:~$ sudo dhclient -r wlan0 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
[COLOR="Red"]Listening on LPF/wlan0/00:15:af:12:7d:b7 
Sending on   LPF/wlan0/00:15:af:12:7d:b7 
Sending on   Socket/fallback 
DHCPRELEASE on wlan0 to 192.168.0.1 port 67 
send_packet: Network is unreachable 
send_packet: please consult README file regarding broadcast address. [/COLOR]

dexter@dexim-laptop:~$ sudo ifconfig wlan0 
[COLOR="Red"]wlan0     Link encap:Ethernet  HWaddr 00:15:AF:12:7D:B7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
[/COLOR]

dexter@dexim-laptop:~$ sudo iwconfig wlan0 essid "NETGEAR" 
dexter@dexim-laptop:~$ sudo iwconfig wlan0 key HEX_KEY 
Error for wireless request "Set Encode" (8B2A) : 
    invalid argument "HEX_KEY". 

dexter@dexim-laptop:~$ sudo iwconfig wlan0 mode managed 

dexter@dexim-laptop:~$ sudo dhclient wlan0 
There is already a pid file /var/run/dhclient.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:15:af:12:7d:b7 
Sending on   LPF/wlan0/00:15:af:12:7d:b7 
Sending on   Socket/fallback 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
[COLOR="Red"]No DHCPOFFERS received. 
No working leases in persistent database - sleeping[/COLOR]. 
dexter@dexim-laptop:~$

p[B]s: I have also tried loading Ndiswrapper and the latest Realtek 8187B driver for W98. When I invoke "sudo ndiswrapper -l" in a terminal, I get:
net8187b : driver installed
device (0BDA:8187) present (alternate driver rtl8187)

net rtuw : driver installed
device 0BDA:8187) present (alternate driver rtl8187)[/B]

Does this mean I have two separate Ndiswrapped drivers loaded?
Cheers

---

