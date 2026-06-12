---
title: "How do I connect to my Internet ( Need help please ! )"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by dafuqmanlolz on 2013-12-30
Hey so today I decided to move from windows 7 to linux. Those main reason was because I personally think linux is better and I have a Compag nx 7400.
Spec :
Intel Core 2 Duo 1.67GHz Proccesor.
Ram 1
GPU : Intel GMA 950 251MB.

_______________________________________________________________________________________________________________________________

So okay, I am on ubuntu testing mode on (USB) and my internet works here throught cable.
When I go on my installed Ubuntu there is 2 big problems.

1. My wireless internet won't work! So I can't find connections all of my other family members are using it (but on windows) . So I press on my Wireless activator button/Switch but no blue light no nothing apears no wireless why ? That didn't happen on windows please solution :( .
2. My cable internet doesn't connect why how do I set it up please help ! I want this done before new years.



Thank you 


Regards Ovidiu.

---

### Post by dafuqmanlolz on 2013-12-30
Hey so today I decided to move from windows 7 to linux. Those main  reason was because I personally think linux is better and I have a  Compag nx 7400.
Spec :
Intel Core 2 Duo 1.67GHz Proccesor.
Ram 1
GPU : Intel GMA 950 251MB.

__________________________________________________   __________________________________________________   ___________________________

So okay, I am on ubuntu testing mode on (USB) and my internet works here throught cable.
When I go on my installed Ubuntu there is 2 big problems.

1. My wireless internet won't work! So I can't find connections all of  my other family members are using it (but on windows) . So I press on my  Wireless activator button/Switch but no blue light no nothing apears no  wireless why ? That didn't happen on windows please solution :sad: .
2. My cable internet doesn't connect why how do I set it up please help ! I want this done before new years.



Thank you 


Regards Ovidiu.

---

### Post by QIII on 2013-12-30
[I]Threads [B]Merged.


[/B][/I]Please do not post identical threads in different areas of the forum.  If you posted in what you feel was the wrong place, please use the "Report Post" button and ask the staff to move your post to a better place.

---

### Post by Iowan on 2013-12-30
Please copy/paste (preferably in code tags) the results of the following commands (from a terminal):
```
ifconfig
sudo lshw -C network
```
I probably missed a few, but it's a start.

---

### Post by dafuqmanlolz on 2013-12-30
```
    ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth4
       version: 02
       serial: 00:17:08:44:de:5e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.104 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:f4108000-f4109fff
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ ^C
ovidiu@ovidiu-HP-Compaq-nx7400-RW215US-ABA:~$ ifconfig
eth4      Link encap:Ethernet  HWaddr 00:17:08:44:de:5e  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe44:de5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6255305 (6.2 MB)  TX bytes:964940 (964.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98454 (98.4 KB)  TX bytes:98454 (98.4 KB)


```

---

