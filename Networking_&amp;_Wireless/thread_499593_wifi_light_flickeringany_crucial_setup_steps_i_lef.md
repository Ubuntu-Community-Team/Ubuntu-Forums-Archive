---
title: "wifi light flickering/any crucial setup steps i left out?"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by S15_88 on 2007-07-12
finished installing ndiswrapper/the driver and got a bunch of stuff figured out now i'm in a little bit of a tickle.  I don't have a wireless router here at home i can manage with a 25' long ehternet jus fine with my laptop as i live in a tiny apartment haha the purpose of configuring my wireless is for next year when i got to university, to study computer science very excited by the way, the whole campus is wireless.

So I was wondering what the deal is with the wifi light flickering? my bluetooth light is solid so why wifi goin haywire?

a total nooob question but how do i see wifi signals/possibly connect to an unsecured one?  right now i've got wifi-radar installed and can see like 20 connections from ppl in my building most of which aren't secured [-X. but how do i use gnome-network-manager, also it won't let me configure the lo connection? is that normal?

here is a bunch of output that you may find useful if you need to reference anything:

Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

> 
alain@S15:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

alain@S15:~$ ndiswrapper -l
netw4x32 : driver installed
        device (8086:4229) present


**/etc/network**
> 
auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#Wiface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0

iface eth0 inet manual


> 
alain@S15:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:19:89:39
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.47+Intel,04/30/2007,11.1.1.11 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:efdfe000-efdfffff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:7a:3c:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 multicast=yes
       resources: iomemory:ef9fe000-ef9fffff irq:17


> 
alain@S15:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=150 Mb/s   
          Fragment thr=1500000 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks, Alain

---

### Post by sj3fk3 on 2007-07-13
> **S15_88 said:**
> 
a total nooob question but how do i see wifi signals/possibly connect to an unsecured one?  
Thanks, Alain

so far, so good.. Try installing the gnome network manager, that does help setting up a connecting. If you just wanna see whats around typing 'iwlist scan' does the trick also.

---

