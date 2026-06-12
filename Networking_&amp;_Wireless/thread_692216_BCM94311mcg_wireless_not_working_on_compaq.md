---
title: "BCM94311mcg wireless not working on compaq"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by ak_saravanan on 2008-02-09
Hi, 
I recently bought compaq laptop that came with BCM94311MCG wireless card. It works fine with preinstalled windows xp software(which i don't like), so installed latest ubuntu and followed a link to make my wireless work, but i didn't 
here is the link i followed 
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/)

prior to this i attempted an installed bcm4311 using ndiswrapper . which didn't work either.

now i don't know if my previous failed attempt is causing further success .. 

can somebody help me.
thanks
AK


lspci - > 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

my /etc/network/interfaces
#auto lo
#iface lo inet loopback
auto lo
iface lo inet loopback
iface eth1 inet dhcp
wireless-key xxxxxx
wireless-essid yyyy
auto eth1
iface wlan0 inet dhcp
wireless-key xxxxx
wireless-essid yyyy
auto wlan0

iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1B:38:93:56:31  
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe93:5631/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4120774 (3.9 MB)  TX bytes:447770 (437.2 KB)
          Interrupt:22 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Hightide on 2008-02-09
Hi ak_saravanan

Have you tried the[ Broadcom]("http://ubuntuforums.org/showthread.php?t=405990") tutuorial?

could you post output from 

lshw -C network


regards
:)

---

### Post by ak_saravanan on 2008-02-09
Hi , is ouput of lshw -C network

BTW, the link you talk about Broadcom tutorial, is for bcm4311.
i have BCM94311. i am not sure, if they both are same or different.
i have just reinstalled ubuntu 7.10 and retrying whole thing, haven't start yet

thx
AK


pradhyu@pradhyu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:00:00:1a:73:c5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 10
       serial: 00:1b:38:93:56:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.71 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

---

### Post by ak_saravanan on 2008-02-09
hi

after reinstalling ubuntu and following steps i mentioned my wireless network works

but i don't have option to enter my wep key from network manager icon

it has only web 128 bit, pass phrase
wep 64/128 hex
wep 64/128 ascii
LEAP

i tried all and it doesn't connect to my network.

i have another system where i set this to make it work (all manually)

ifconfig wlan1 down
iwconfig wlan1 essid ... key  xxx
ifconfig  wlan1 up
dhclient3 wlan1

i hope this will work for me

thx
AK

---

### Post by ak_saravanan on 2008-02-09
hi

after reinstalling ubuntu and following steps i mentioned my wireless network works

but i don't have option to enter my wep key from network manager icon

it has only web 128 bit, pass phrase
wep 64/128 hex
wep 64/128 ascii
LEAP

i tried all and it doesn't connect to my network.

i have another system where i set this to make it work (all manually)

ifconfig wlan1 down
iwconfig wlan1 essid ... key  xxx
ifconfig  wlan1 up
dhclient3 wlan1

i hope this will work for me

thx
AK

---

### Post by ak_saravanan on 2008-02-09
hi

after reinstalling ubuntu and following steps i mentioned my wireless network works

but i don't have option to enter my wep key from network manager icon

it has only web 128 bit, pass phrase
wep 64/128 hex
wep 64/128 ascii
LEAP

i tried all and it doesn't connect to my network.

i have another system where i set this to make it work (all manually)

ifconfig wlan1 down
iwconfig wlan1 essid ... key  xxx
ifconfig  wlan1 up
dhclient3 wlan1

i hope this will work for me

thx
AK

---

