---
title: "having trouble with wireless card"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by untappedpilot2 on 2008-10-09
I'm currently using a RTL8185 chipset wireless card and I'm having trouble getting it to find an AP. I'm trying to use the mac80211 rtl8180 driver which should be compatible for this card and it seems like it's been installed properly. Here's some info with what's goin on...

derek@derek-laptop:~$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:0a:e4:41:aa:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.103 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 20
       serial: 00:18:e7:28:d8:20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg


derek@derek-laptop:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


derek@derek-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:41:aa:bc  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe41:aabc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45342234 (43.2 MB)  TX bytes:1853983 (1.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13500 (13.1 KB)  TX bytes:13500 (13.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:e7:28:d8:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-E7-28-D8-20-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


derek@derek-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results



I only have one wireless device and it looks like my card is being dual associated as "wmaster0" and "wlan0". What can I do about this? I've looked all over and similar questions have gone unanswered or there's nothing about it. Any help would be greatly appreciated.

---

### Post by untappedpilot2 on 2008-10-09
Well after poking around on the forums for awhile I managed to solve my problem by a shot in the dark... it actually seems that many more than just me are having the same problem with no response. 

First I noticed that when I would do iwlist scan I wouldn't get any results.. However if I did sudo iwlist scan It would pick up my AP on wlan0. So all I did was open the Network Manager and take it off Roaming Mode. Even though it wouldn't show my ESSID in the drop-down I manually entered my ESSID and network key. Presto! It picked it up and connected.

I actually had this card working with ndiswrapper but I wanted to switch to the mac80211 driver since it is compatible with aircrack-ng. But even when I was using ndiswrapper I couldn't get my connection to work in roaming mode. However with ndiswrapper it would pick up my network and show my ESSID in the drop-down when I went to configure my network.

Hope this helps someone else!

---

### Post by pozer69 on 2009-01-10
> **untappedpilot2 said:**
> 
I actually had this card working with ndiswrapper but I wanted to switch to the mac80211 driver since it is compatible with aircrack-ng. 

Did you ever make a driver for the RTL8185 with the mac80211? I dont know how to compile drivers bc Im a noob but I want to be able to use aircrack. i have aircrack installed but i receive the following error:

-e Interface	Chipset		Driver

wlan0		Unknown		Unknown

---

