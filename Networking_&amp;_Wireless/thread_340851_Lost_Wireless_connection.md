---
title: "Lost Wireless connection"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by keet on 2007-01-17
Hi folks recently installed and was running Edgy Eft beautifully wirelessly via Netgear DG834 GT  WAP, and Wg311T pci adapter. Now the only way that  i can connect is via a patch cable. 
I think that i may have also lost Network Manager (i.e. System, Administration, Networking)
I include below output for iconfig, and iwconfig from terminal. Can some one please hav a look and see what/where/how  i got myself into this position and what i need to do to resolve. Thanks Leroy.

@leroy-desktop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:6C:30:20:AA  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fe30:20aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:156831 (153.1 KiB)  TX bytes:43230 (42.2 KiB)

eth0      Link encap:Ethernet  HWaddr 00:15:F2:00:59:EB  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe00:59eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1796141 (1.7 MiB)  TX bytes:221731 (216.5 KiB)
          Interrupt:217 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33281 (32.5 KiB)  TX bytes:33281 (32.5 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.4.1  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.245.1  Bcast:192.168.245.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-30-20-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31343 errors:0 dropped:0 overruns:0 frame:647
          TX packets:652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3611363 (3.4 MiB)  TX bytes:68419 (66.8 KiB)
          Interrupt:58 Memory:f8a60000-f8a

@leroy-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"leroy"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:14:6C:AD:2F:0C   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/94  Signal level=-40 dBm  Noise level=-95 dBm
          Rx invalid nwid:10  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

leroy@leroy-desktop:~$

---

### Post by teaker1s on 2007-01-20
install
network-manager-gnome


now on your desktop panel you want to click system administration networking

it's important to make sure that devices show unconfigured so network-manager-gnome can control them. Shutdown and remove ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in passphrase or network key
_

---

