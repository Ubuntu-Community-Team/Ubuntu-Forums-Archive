---
title: "Wireless problem, packets being droped [tried everything I could find:(]"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by H1tm3n on 2008-06-06
I could not find solution to this problem, I tried everything I could (all stickies). Search is not very helpful, because I can't specify the problem very well in 2-3 words


the problem is that when I ping router or any other address on this local network (there is local network 255.255.255.0 192.168.1.1, and to that network wireless router is connected as a SWITCH, that is: an extension to the previous one, and I'm trying to establish connection to that router with hardy here). 

For Windows (and for everybody else) everything works flawlessly (perfectly).

when I try to ping router OR the main gateway of LAN (I'm not sure how could he distinguish those, but I get the same results pinging anyone else)

pinging results:

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable
From 192.168.1.102 icmp_seq=4 Destination Host Unreachable
From 192.168.1.102 icmp_seq=5 Destination Host Unreachable
From 192.168.1.102 icmp_seq=6 Destination Host Unreachable
From 192.168.1.102 icmp_seq=7 Destination Host Unreachable
From 192.168.1.102 icmp_seq=8 Destination Host Unreachable
From 192.168.1.102 icmp_seq=9 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
11 packets transmitted, 0 received, +9 errors, 100% packet loss, time 10033ms
, pipe 3
```

These configs are after I configured network manualy (with the sticky post)

But I didn't do "dhclient ath0" because after that I loose even the IP I have now. That is there is no DHCP response (it does not connect or whatever else)

ifconfig:

```
ath0      Link encap:Ethernet  HWaddr 00:15:af:7d:d7:35  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe7d:d735/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:30 dropped:30 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3912 (3.8 KB)  TX bytes:11454 (11.1 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:8c:92:b6:4d  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe92:b64d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15430627 (14.7 MB)  TX bytes:2984880 (2.8 MB)
          Interrupt:218 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:60038 (58.6 KB)  TX bytes:60038 (58.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-7D-D7-35-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29625 errors:0 dropped:0 overruns:0 frame:74
          TX packets:5972 errors:0 dropped:30 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3305844 (3.1 MB)  TX bytes:435382 (425.1 KB)
          Interrupt:17 

```

iwconfig

```
ath0      IEEE 802.11g  ESSID:"S. Teresa"  Nickname:""
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:18:F8:C7:C7:79   
          Bit Rate:48 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-47 dBm  Noise level=-96 dBm
          Rx invalid nwid:5084  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Not sure what to fix here. Any help would be appreciated!

Here's what I have:
```

Ethernet controller		: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter 
Ethernet controller		: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 
FireWire (IEEE 1394)		: Ricoh Co Ltd R5C832 IEEE 1394 Controller 
```

---

### Post by chili555 on 2008-06-06
Please see here: [https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager) especially this:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themNotice you have an IP address and connectivity on your wired interface?> eth0      Link encap:Ethernet  HWaddr 00:1e:8c:92:b6:4d  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe92:b64d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24945 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15430627 (14.7 MB)  TX bytes:2984880 (2.8 MB)
          Interrupt:218 Base address:0xe000 
I think you are being 'managed'! Please detach the wire, reboot and see if you wireless works now.

---

### Post by H1tm3n on 2008-06-06
Thanks for reply! but unfortunately that would be too simple. I tried with eth0 down, also (now) manualy unplugging, restarting, just like you said and more... nothing seem to work...

and yet I seem to be so close... even access point is associated (or at least it says so)

There 2 things I noticed, that could be wrong

I'm using Atheros AR5007EG wireless card, and in drivers instalation manual it says that I have to disable Atheros hardware access layer (HAL), but even if I unthick it, it still says it is in use....

2 or 3 times there was this additional interface for wireless connection (like showing strenght of the signal in tray and additional options on right click on network configurator in tray) but I cannot bring them back whatever I do

Hope that says something for you guys. Will be waiting for any suggestions... thank you in advance!

---

