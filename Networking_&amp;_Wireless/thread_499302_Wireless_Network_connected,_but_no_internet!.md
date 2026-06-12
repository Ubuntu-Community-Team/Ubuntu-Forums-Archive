---
title: "Wireless Network connected, but no internet!"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by secretspicy15 on 2007-07-12
Ok, I have searched everywhere and have not found a problem quite like mine., (If there is a thread about this somewhere, I am sorry, I *did* search, to no avail...)

I had been happily running edgy for a while and it was great it could connect to the internet fine etc, but when I updated to fesity BAM! nothing works. It shows that I am connected to the network, however I have no internet access, I cannot ping anything. From other posts I have gleaned that I probably have a DHCP problem, but no one seems to give any information on how to fix this kind of thing. I have tried all of the usual fixes ad nauseaum (ifdown ifup, etc) and nothing works. I had to resign to use windows for the remainder of the quarter because I was too busy with school. I am now at home and have just now had the time to mess with it and I cannot find any solutions what so ever.

If anyone has any ideas, please let me know. I am sure you will want some kind of output from various commands; just let me know what you need...

Thanks!!!

TJ

---

### Post by kevdog on 2007-07-12
You got to tell us more about your system, wireless card name, how you installed the drivers, etc.  

Also post the following
lshw -C network
iwlist scan
/etc/network/interfaces

That would be a start!  Im sure I will need more later.  You need to be more specific and detail oriented when asking for help.

---

### Post by netreg on 2007-07-12
It may also be worthwhile checking what you have as your DNS servers...

---

### Post by secretspicy15 on 2007-07-12
> **kevdog said:**
> You got to tell us more about your system, wireless card name, how you installed the drivers, etc.  

Also post the following
lshw -C network
iwlist scan
/etc/network/interfaces

That would be a start!  Im sure I will need more later.  You need to be more specific and detail oriented when asking for help.

Ok, sorry about that, I wasn't sure what would be needed and I don't know enough about the problem to be specific...

I have a dell inspiron e1705 dual booting Feisty and XP. I did not install any extra drivers, it detects the signal from the wireless, it just cannot connect to the internet. I did not have to install any additional drivers in edgy to get it to work either...

And the outputs you requested:

```
tj@tj-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:98:b8:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.200.249 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ecfff000-ecffffff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:37:46:29
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:ecbfe000-ecbfffff irq:17
```

```
tj@tj-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:56:FC:CF
                    ESSID:"ellis"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-63 dBm  Noise level=-63 dBm
                    Extra: Last beacon: 48ms ago


```

/etc/network/interfaces:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
address 10.87.2.19
netmask 255.0.0.0

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth1 inet dhcp
wireless-essid ellis
address 192.168.200.252
netmask 192.168.200.0
wireless-key s:*********

auto eth1



```

Any ideas you may have would be greatly appreciated, once more thanks for all of your help and thank you for being patient; I am still relatively new to both linux and networking...

Thanks!:KS

TJ

---

### Post by secretspicy15 on 2007-07-12
Also, since they have been asked for on most other posts with networking/internet connection problems here are the outputs from running dhclient and ifconfig:

```
tj@tj-laptop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 7072
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:c5:37:46:29
Sending on   LPF/eth0/00:15:c5:37:46:29
Listening on LPF/eth1/00:13:02:98:b8:bf
Sending on   LPF/eth1/00:13:02:98:b8:bf
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.200.1
bound to 192.168.200.249 -- renewal in 32630 seconds.

tj@tj-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:37:46:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:13:02:98:B8:BF  
          inet addr:192.168.200.249  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe98:b8bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:71 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52669 (51.4 KiB)  TX bytes:2992 (2.9 KiB)
          Interrupt:17 Base address:0xe000 Memory:ecfff000-ecffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)

```

Thanks again!

---

### Post by kevdog on 2007-07-12
Its the wireless thats not working correct??

Couple of things:
iface eth1 inet dhcp
wireless-essid ellis
address 192.168.200.252
netmask 192.168.200.0
wireless-key s:*********

auto eth1

The above implies you are using WEP.  Also I dont think the netmask is correct, and you are missing a gateway statement.  Netmasks are usually 255.255.255.0.  Also I dont know if you essid name needs to be in quotes.

What happens if you just turn WEP off for the meantime and then just use
auto eth1
iface eth1 inet dchp

If you need to use a static address it would be more like
iface eth1 inet static

---

### Post by secretspicy15 on 2007-07-12
Ok, I tried that, however now I cannot connect to the network at all. Before I could connect to the network, it showed me connected to the network with a strong signal, and showed communication on the network, packets sent recieved etc, I just had no internet access. Now (after changing the network interface file) it does not connect at all.

---

### Post by secretspicy15 on 2007-07-12
Well, I reactivated WEP and edited the interface file to include the necessary information again. I corrected the netmask and added the correct gateway. It once more shows me connected to the network but I am still unable to access the internet or ping anything.

Thank you again for your time and advice!

---

### Post by secretspicy15 on 2007-07-16
*BUMP* I'm still having the same problem; the Network Manager shows me connected to the network, but I have no internet access whatsoever. I don't beleive it is a problem with the network itself since I'm using it now on my windows boot. If anyone has any ideas PLEASE let me know.

Thank you!
TJ

P.S. Actually if anyone knows an easy way to reinstall edgy (maybe without wiping out everything[-o< ) let me know too. that might be the only way to fix this, or at least the easiest way...

---

### Post by secretspicy15 on 2007-07-17
I gave in and reinstalled edgy. Everything is fine now. Thanks anyway for the help.

---

### Post by kevdog on 2007-07-17
Sorry you couldnt get it working.

---

### Post by secretspicy15 on 2007-07-17
'sok, now I'm on edgy, happily back to ubunutu:KS

---

