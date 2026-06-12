---
title: "wireless broadcom 4311 problem please help..."
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by bvidinli on 2007-05-05
hi,
i read so many guides..
i did so many things...

but my broadcom 4311 wireless adapter is not functioning properly.

here is my info:
root@bvidinli-laptop:/home/bvidinli# lspci | grep Broadcom
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
10:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)


i was using ubuntu 6.10, upgraded to 7.04 using update-manager -d
my notebook is hp compaq nc8430


i was not able to use my wless in ubuntu 6.10 or 7.04
so i tried ndiswrapper

now i use ubuntu 7.04 desktop edition
root@bvidinli-laptop:/home/bvidinli# uname -a
Linux bvidinli-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux


root@bvidinli-laptop:/home/bvidinli# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present

root@bvidinli-laptop:/home/bvidinli# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:08:4C:A2:E3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe4c:a2e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2450897 (2.3 MiB)  TX bytes:438544 (428.2 KiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:992 (992.0 b)  TX bytes:992 (992.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:01:29:BE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:f4000000-f4004000 

wlan0:ava Link encap:Ethernet  HWaddr 00:1A:73:01:29:BE  
          inet addr:169.254.5.94  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:f4000000-f4004000 



root@bvidinli-laptop:/home/bvidinli# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@bvidinli-laptop:/home/bvidinli# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results





please help..

---

### Post by bvidinli on 2007-05-05
finally solved...

thanks to everybody who wrote those howtos:
this howt helped:
[http://ubuntuforums.org/showthread.php?t=297092&page=3](http://ubuntuforums.org/showthread.php?t=297092&page=3)
bu adresteki su yazi yardimci oldu:
meger, notebookun wless mereti kapali kaliyormus... 
off nihayet calisti..

Reboot your machine. BEFORE it starts loading linux, go in to your BIOS setup. Scroll down to the entry that says Wireless. You'll see a section that says something about the Wifi / bluetooth hotkey. Try setting that so that the wifi is always on, and the hotkey is disabled.


root@bvidinli-laptop:/var/log# iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"USR9108"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:C1:05:06:A4   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:6261-6868-37   Security mode:restricted
          Power Management:off
          Link Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@bvidinli-laptop:/var/log# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1A:73:01:29:BE  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe01:29be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1082533 (1.0 MiB)  TX bytes:184180 (179.8 KiB)
          Interrupt:17 Memory:f4000000-f4004000 

root@bvidinli-laptop:/var/log# ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=240 time=174 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=240 time=174 ms

--- google.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2005ms
rtt min/avg/max/mdev = 174.140/174.294/174.449/0.445 ms
root@bvidinli-laptop:/var/log#

---

