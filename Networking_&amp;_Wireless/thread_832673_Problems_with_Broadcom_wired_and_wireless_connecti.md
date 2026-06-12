---
title: "Problems with Broadcom wired and wireless connection"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by aethyrah on 2008-06-17
I just finished installing Ubuntu 8.04 LTS, and my internet doesn't work!

I can plug my internet into the port and nothing happens.  I'm not sure if the wireless is even configured right.  Newbie to Linux and I need some help to get both of my connections up and running. 

I've been having trouble getting my wired and wireless connections working. Both are Broadcom chipsets.

---

### Post by aethyrah on 2008-06-18
When I run lshw -C network this is what I get:

WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 01
       serial: 00:03:25:0c:bc:b6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:f5:0e:16:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by aethyrah on 2008-06-18
lspci |grep Broadcom

00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0e.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by Pjotr123 on 2008-06-18
The problem is, you need internet to get your wireless working. I can't help you with the *wired* connection trouble. But when you have succeeded in that, do this for the wireless:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by superprash2003 on 2008-06-18
go to the terminal and type ifconfig and post output.. also type iwconfig and post output

---

### Post by aethyrah on 2008-06-18
Here is the output from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:03:25:0c:bc:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73100 (71.3 KB)  TX bytes:73100 (71.3 KB)



Here is the output from iwconfig:

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by superprash2003 on 2008-06-18
is dhcp enabled in your router? if so go to system->administration->Network->eth0 properties-> set it to DHCP mode from roaming.. and then post ifconfig output

---

### Post by aethyrah on 2008-06-18
I'm not a home right now, i'll have to check it once I get off work and before I head to class this evening.

---

