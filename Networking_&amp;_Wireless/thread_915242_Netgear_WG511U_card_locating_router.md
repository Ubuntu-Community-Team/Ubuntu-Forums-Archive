---
title: "Netgear WG511U card locating router"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by mcld on 2008-09-09
My Netgear WG511U card seems to work fine (fresh install of Xubuntu 8.04) - it appears in "Network" settings and happily allows me to set the ESSID etc etc. But it cannot find the wireless router (1m away from the laptop!). Here are some details:

from lspci:
06:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

from iwconfig:
ath0      IEEE 802.11a  ESSID:"G604T_WIRELESS"  Nickname:""
          Mode:Managed  Frequency:5.2 GHz  Access Point: 00:11:95:94:99:E0   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:[i've hidden it, but it's correct]   Security mode:restricted
          Power Management:off
          Link Quality=0/70  Signal level=-90 dBm  Noise level=-90 dBm
          Rx invalid nwid:15348  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

from ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:0f:b5:3e:31:88  
          inet6 addr: fe80::20f:b5ff:fe3e:3188/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:0f:b5:3e:31:88  
          inet addr:169.254.5.160  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22700 (22.1 KB)  TX bytes:22700 (22.1 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-B5-3E-31-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19155 errors:0 dropped:0 overruns:0 frame:1804
          TX packets:19299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2269079 (2.1 MB)  TX bytes:945818 (923.6 KB)
          Interrupt:11 


These outputs look "happy", so why can't it see the router? :(

---

