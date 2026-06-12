---
title: "[SOLVED] No wired connection after upgrade to 8.10"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by him610 on 2008-11-11
Symptoms: Wired onboard ethernet connection not working; one amber LED and one green LED indicated.

Seems to have occurred about the time of the upgrade to 8.10; just never took the time to investigate since I still had an operational wireless connection. The onboard ethernet connection is controlled by the Nvidia MCP67 chip; it also controls everything else on the mainboard.

1.  During the course of the investigation, the cat-5 cable was substituted for a known good one to no avail.

2.  Noted that an updated Nvidia accelerated graphics driver (version 177)[Recommended] had been installed during the upgrade to 8.10.

3.  Deactivated version 177, and reinstalled (previous) version 173. This was accomplished using the Hardware Drivers GUI tool.

4.  Regained use of onboard ethernet connection upon installation and activation of Nvidia accelerated graphics driver (version 173).

5.  Discovered there is one more thing that needs to be accomplished; since both connections, wired and wireless were now operational, one of them had to be shutdown. I chose to shutdown the wireless connection since it is the slower of the two (54mbs v. 100mbs).

6.  There is a downside to this process; when you deactivate version 177, you lose the upgraded graphics capability.  

I have documented all of the steps I used from the CLI to get a working connection again, inserting comments where appropriate. I thought maybe I might be able to help someone.

Cheers.

```
hughm@shuttle-desktop:~$ lspci 
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7025 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

hughm@shuttle-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:85:0a:96:66  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe0a:9666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3600 (3.6 KB)  TX bytes:17734 (17.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-85-0A-96-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

hughm@shuttle-desktop:~$ sudo ifdown lo
[sudo] password for hughm: 
hughm@shuttle-desktop:~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:14:85:0a:96:66  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe0a:9666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3702 (3.7 KB)  TX bytes:18230 (18.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-85-0A-96-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

hughm@shuttle-desktop:~$ sudo ifup lo
hughm@shuttle-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:85:0a:96:66  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe0a:9666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3702 (3.7 KB)  TX bytes:18726 (18.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-85-0A-96-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

# This is the point where Nvidia acclerated graphics driver (version 177)[Recommended] was deactivated,  and Nvidia acclerated graphics driver (version 173) was activated

hughm@shuttle-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bc:51:b8  
          inet6 addr: fe80::230:1bff:febc:51b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:567 (567.0 B)  TX bytes:492 (492.0 B)
          Interrupt:247 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5800 (5.8 KB)  TX bytes:5800 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:85:0a:96:66  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe0a:9666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16289801 (16.2 MB)  TX bytes:577259 (577.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-85-0A-96-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

hughm@shuttle-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
hughm@shuttle-desktop:~$ sudo ifup eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:30:1b:bc:51:b8
Sending on   LPF/eth0/00:30:1b:bc:51:b8
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.4 from 192.168.1.1
DHCPREQUEST of 192.168.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.4 from 192.168.1.1
bound to 192.168.1.4 -- renewal in 2147483648 seconds.
hughm@shuttle-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bc:51:b8  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:febc:51b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2531 (2.5 KB)  TX bytes:10113 (10.1 KB)
          Interrupt:247 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5800 (5.8 KB)  TX bytes:5800 (5.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:85:0a:96:66  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fe0a:9666/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16300816 (16.3 MB)  TX bytes:578835 (578.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-85-0A-96-66-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

# This is where the wireless connection gets shutdown.

hughm@shuttle-desktop:~$ sudo ifdown wlan0
[sudo] password for hughm: 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4704
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:85:0a:96:66
Sending on   LPF/wlan0/00:14:85:0a:96:66
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
hughm@shuttle-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=22 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

hughm@shuttle-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bc:51:b8  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:febc:51b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:363 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71617 (71.6 KB)  TX bytes:11500 (11.5 KB)
          Interrupt:247 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6400 (6.4 KB)  TX bytes:6400 (6.4 KB)

hughm@shuttle-desktop:~$ ping -c 4 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=238 time=39.1 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=238 time=37.7 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=238 time=38.3 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=238 time=48.4 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 37.789/40.916/48.426/4.361 ms


```

---

### Post by directcharitycontribution on 2008-11-13
u try sum tags?

---

