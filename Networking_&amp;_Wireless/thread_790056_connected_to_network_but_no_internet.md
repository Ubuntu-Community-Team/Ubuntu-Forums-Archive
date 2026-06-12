---
title: "connected to network but no internet"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by rm00re on 2008-05-11
First off this is my first experience with Linux (Ubuntu 8.04) so I apologies in advance for my ignorance.
I’m using a NETGEAR WG111 v2 wireless card. I can connect to wireless networks fine but I never get internet. I get “page load error” and “firefox can’t find the server.” I've been on to different routers that work fine in XP but not in Ubuntu so I know it's not the router.

Here’s what I’ve found so far
```

~$ lsusb 
Bus 004 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2) 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:009f Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:93:a9:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:3430 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3430 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:185242 (180.9 KB)  TX bytes:185242 (180.9 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:b7:5a:17  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::20f:b5ff:feb7:5a17/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2108 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1223 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:299702 (292.6 KB)  TX bytes:135898 (132.7 KB) 

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-B7-5A-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

~$ lspci 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) 
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02) 
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) 
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02) 
02:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01) 

~$ ping -c www.google.com 
ping: bad number of packets to transmit. 

~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: 82562EZ 10/100 Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 02 
       serial: 00:0c:6e:93:a9:c8 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes 
  *-network 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:0f:b5:b7:5a:17 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11g 
```
 
Any help getting this working would be greatly appreciated. I’ve really enjoyed Ubuntu but if I don’t get this fixed it’s back to XP

---

### Post by .rdg on 2008-05-11
You can test your networking with a couple easy steps. Every command I will present here must be written in Terminal (it's installed and available in Ubuntu Apps menu). So the steps with short descriptions what are they for:

1. Check your routing table with: netstat -rn

Sample output:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0    0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1    0.0.0.0         UG        0 0          0 wlan0

The important info is in the last line - destination 0.0.0.0 (which is just anything) is reached through 192.168.1.1 (your default Gateway). This address is important.

2. Ping the gateway with: ping 192.168.1.1 (or what you received from step 1).

Sample output:
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.67 ms

This tells you don't have connectivity problems with your router.

4. Test if your DNS is working OK: nslookup [www.google.com](www.google.com)

Sample output:

Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
[www.google.com](www.google.com)  canonical name = [www.l.google.com](www.l.google.com).
Name:   [www.l.google.com](www.l.google.com)
Address: 209.85.129.147
Name:   [www.l.google.com](www.l.google.com)
Address: 209.85.129.104
Name:   [www.l.google.com](www.l.google.com)
Address: 209.85.129.99

4. Test where the traffic for any site ([www.google.com](www.google.com) perhaps?) ends: mtr [www.google.com](www.google.com)

If you're still not sure where your problem lies just post what you get from each of the steps with one additional command's printout: ifconfig. Hope that helps.

---

### Post by rm00re on 2008-05-11
After a reboot this morning everything's working. Connects to the network and I have full internet use. For about 5 minutes. Then it’s gone back to “Firefox can’t find the server.” While it was working I ran through the code you posted and everything came back looking good. I ran them again when it was down and this is what I got.
```

~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.103 icmp_seq=1 Destination Host Unreachable
From 192.168.1.103 icmp_seq=2 Destination Host Unreachable
From 192.168.1.103 icmp_seq=3 Destination Host Unreachable
From 192.168.1.103 icmp_seq=5 Destination Host Unreachable
From 192.168.1.103 icmp_seq=6 Destination Host Unreachable
From 192.168.1.103 icmp_seq=8 Destination Host Unreachable
From 192.168.1.103 icmp_seq=9 Destination Host Unreachable
From 192.168.1.103 icmp_seq=10 Destination Host Unreachable
From 192.168.1.103 icmp_seq=12 Destination Host Unreachable
From 192.168.1.103 icmp_seq=13 Destination Host Unreachable
From 192.168.1.103 icmp_seq=14 Destination Host Unreachable
From 192.168.1.103 icmp_seq=15 Destination Host Unreachable
From 192.168.1.103 icmp_seq=16 Destination Host Unreachable
From 192.168.1.103 icmp_seq=17 Destination Host Unreachable
From 192.168.1.103 icmp_seq=20 Destination Host Unreachable
From 192.168.1.103 icmp_seq=21 Destination Host Unreachable
From 192.168.1.103 icmp_seq=23 Destination Host Unreachable
From 192.168.1.103 icmp_seq=24 Destination Host Unreachable
From 192.168.1.103 icmp_seq=25 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
26 packets transmitted, 0 received, +19 errors, 100% packet loss, time 25027ms
, pipe 3

~$ nslookup www.google.com
;; connection timed out; no servers could be reached

~$ mtr www.google.com
Name or service not known: No such file or directory
rm00re@rm00re-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:93:a9:c8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:135066 (131.9 KB)  TX bytes:135066 (131.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:b5:b7:5a:17  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:feb7:5a17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2567 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2082617 (1.9 MB)  TX bytes:466793 (455.8 KB)
wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-B7-5A-17-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```
Any ideas? After another restart I got the same thing maybe 5 minutes of internet then it’s gone, I’m still on the network but no internet access. Also I think I can get the output from when it's working if that helps (by rebooting again.)

---

### Post by .rdg on 2008-05-11
The problem is with your wifi card - your IP address and routing table are fine. Perhaps you're using the wifi card, which doesn't have any Open Source drivers so you'll stuck with ndiswrapper. If it's so this may happen, because this solution is unstable. I had the same issue, but fortunately with 8.04 my wifi card has already an Open Source driver which now works like a charm.

---

### Post by martin15s on 2008-05-11
after numerous problems in 7.10 and 8.04 with usb and built in wlan on my laptop and intermittent successes I bought an Edimax Ew--7108PCG pcicmia card (not expensive) and in 8.04 works straight from the box - all problems solved - try it and DO NOT go back to windows.

---

### Post by rm00re on 2008-05-11
I looked into drivers and found a lot of problems getting a Netgear WG111v2 working. But they had no network connection, and the solutions were not for 8.04 (as in they're known not to work with 8.04) any body got a WG111v2 working with hardy?

---

### Post by delphis on 2008-05-15
In your network checking steps you suggest:

4. Test if your DNS is working OK: nslookup [www.google.com](www.google.com)

What do you suggest if the output is:

$ nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached


I can connect to google via a web browser using its IP address, but not the name [www.google.com](www.google.com)

Thanks for any help.

---

### Post by Iowan on 2008-05-15
> **delphis said:**
> I can connect to google via a web browser using its IP address, but not the name
Suggests that DNS isn't working properly.  I'll look around for links on setting up OpenDNS.

---

### Post by delphis on 2008-05-15
I followed instructions [here]("http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html"), but no luck.  I have my linux machine connected through a netgear router, through a westell dsl modem (which is in bridge mode), to verizon.  I also have a windows pc attached to the netgear router, and the internet connection is working fine there (using verizon dns).

---

### Post by Chainz on 2008-05-16
> **rm00re said:**
> After a reboot this morning everything's working. Connects to the network and I have full internet use. For about 5 minutes. Then it’s gone back to “Firefox can’t find the server.” While it was working I ran through the code you posted and everything came back looking good. I ran them again when it was down and this is what I got.

Any ideas? After another restart I got the same thing maybe 5 minutes of internet then it’s gone, I’m still on the network but no internet access. Also I think I can get the output from when it's working if that helps (by rebooting again.)


I have something similar, but it's not wireless problem.

After fresh install (Ubuntu 8.04), working on wireless (LinkSys router), I started Firefox and opened few sites (mostly Ubuntu Documentation).
after few minutes (2 or 3) some sites stopped opening, then more stopped opening, after about 5 min. I couldn't open a single page.

I decided to install Opera - exactly same result.

Then I turned to wired connection - still the same!

And now I don't know what might be the problem, since all other computers in the network work fine, windows on the same machine works fine... :'(

---

