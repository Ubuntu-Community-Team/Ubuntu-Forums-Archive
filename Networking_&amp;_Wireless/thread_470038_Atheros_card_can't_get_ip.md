---
title: "Atheros card can't get ip"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Sylar_7 on 2007-06-10
Hi, I'm new to the linux community.  I've loved tinkering and learning, but I'm coming to my wits end on this issue. 

From what I can tell, I have an atheros chipset.  I'm running Ubuntu and I believe this should work without installing other drivers. (I spent the last few days installing ndiswrapper and madwifi and went back to the original drivers, partly because I'm not sure exactly what I'm doing and if it made a difference).  Last night I got the wireless working by uninstalling the network manager and installing wicd manager as suggested in another post here.  Then I started working on getting WAP working as in the sticky post, but I think I really screwed things up somehow as it seemed to get confused getting the static DNS going, and it got so that i couldn't open the wicd manager.

Well this morning I reinstalled Ubuntu to start from scratch.  I uninstalled network manager and installed wicd, thinking that would get my wireless working like last night.  Now i have to use 'dhclient eth0' to get the wired Ethernet to obtain an IP   When I try to get the wireless to connect (broadcast ssid and no security) it won't obtain an IP.  There is nothing in the MAC filter.  

I'm thinking, based on what I've seen and another post, that the wired driver might be trying to take over the wireless driver and causing the problem.  I saw someone was able set the wired to 'enable on wire connection'.  How do you do this?

for iwconfig:
root@herolaptop:/etc/network# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"heronet"  Nickname:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1A:70:E6:6A:02   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-89 dBm  Noise level=-89 dBm
          Rx invalid nwid:3289  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

for ifconfig:
root@herolaptop:/etc/network# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:20:95:C6:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:70 dropped:70 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16998 (16.5 KiB)  TX bytes:13915 (13.5 KiB)

eth0      Link encap:Ethernet  HWaddr 00:11:0A:41:0F:DF  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:aff:fe41:fdf/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8621614 (8.2 MiB)  TX bytes:1931160 (1.8 MiB)
          Interrupt:12 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1090 (1.0 KiB)  TX bytes:1090 (1.0 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-20-95-C6-97-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32986 errors:0 dropped:0 overruns:0 frame:8871
          TX packets:23908 errors:6 dropped:70 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3363593 (3.2 MiB)  TX bytes:1396567 (1.3 MiB)
          Interrupt:15 

iwlist scan:
root@herolaptop:/etc/network# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:46:86:F6:CA
                    ESSID:"Vfr45678"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/94  Signal level=-74 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100200000
          Cell 02 - Address: 00:1A:70:E6:6A:02
                    ESSID:"heronet"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/94  Signal level=-67 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00

cat /etc/network/interfaces:

auto lo
root@herolaptop:/etc/network# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


I hope this can get worked out.  If you have any suggestions or need more information, let me know!
Thanks!

---

### Post by Sylar_7 on 2007-06-10
Nevermind.  I decided to try ndiswrapper one more time and found this wonderful tutorial:
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)
I highly suggest this tutorial to anyone.

now i just need to get encryption working!

---

