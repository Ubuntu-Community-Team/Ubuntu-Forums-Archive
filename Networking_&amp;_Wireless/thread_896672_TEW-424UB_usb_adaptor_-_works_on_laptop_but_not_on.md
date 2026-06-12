---
title: "TEW-424UB usb adaptor - works on laptop but not on desktop? (ndiswrapper)"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by kwilliam on 2008-08-21
I've got a Trendnet TEW-424UB USB WiFi adaptor with a Realtek RTL8187B chipset (usbid: 0bda:8189) that I'm trying to get working with ndiswrapper. After installing ndisgtk and downloading [the driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") recommended on [the ndiswrapper website]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/"), it worked perfectly on my laptop. Performing those same steps installed the wireless adaptor on my newly built desktop, but it cannot connect for some reason. (It can see other networks, and list them in knetworkmanager.) I'm baffled because they both are up-to-date Kubuntu 8.04 installations, only the desktop install is brand new, while the laptop has been upgraded since Feisty.

When I try to connect, it gets to "Activation stage: IP configuration started." and then after a while gives up and displays a balloon saying, "Connection Failure: Could not connect to the network [networkname]."

I'm not sure what output might help debugging this, but here's the output of ifconfig and iwconfig for each computer:

Laptop ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:19:b9:60:a2:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:19:d2:bc:3e:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1146528 (1.0 MB)  TX bytes:385465 (376.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.0 KB)  TX bytes:1100 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:49:12:fc  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe49:12fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84190 (82.2 KB)  TX bytes:39583 (38.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-BC-3E-81-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Desktop ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:14:2a:d8:a4:35  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fed8:a435/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:172070 (168.0 KB)  TX bytes:27107 (26.4 KB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:49:12:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6126 (5.9 KB)  TX bytes:7547 (7.3 KB)
```

Laptop iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:16:B6:AA:74:5A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=98/100  Signal level=-27 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:"fishnet"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:16:B6:AA:74:5A   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Desktop iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

If I have to, I'll just buy a wireless card with Linux support, but since this USB adapter works on my Kubuntu laptop, I'm surprised it can't connect when plugged into the desktop. Some final notes: my home network uses WPA, and I'm having trouble with one other USB device (an ATI RF remote) that worked out-of-the-box on my laptop but not on the desktop, so perhaps it's a USB problem? Also as a final thought, is it possible updating the bios might help? It's an old motherboard that I bought on Ebay, so maybe something in the bios handles USB wrong?

---

### Post by Ayuthia on 2008-08-21
> **kwilliam said:**
> I've got a Trendnet TEW-424UB USB WiFi adaptor with a Realtek RTL8187B chipset (usbid: 0bda:8189) that I'm trying to get working with ndiswrapper. After installing ndisgtk and downloading [the driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true") recommended on [the ndiswrapper website]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/"), it worked perfectly on my laptop. Performing those same steps installed the wireless adaptor on my newly built desktop, but it cannot connect for some reason. (It can see other networks, and list them in knetworkmanager.) I'm baffled because they both are up-to-date Kubuntu 8.04 installations, only the desktop install is brand new, while the laptop has been upgraded since Feisty.

When I try to connect, it gets to "Activation stage: IP configuration started." and then after a while gives up and displays a balloon saying, "Connection Failure: Could not connect to the network [networkname]."

I'm not sure what output might help debugging this, but here's the output of ifconfig and iwconfig for each computer:

Laptop ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:19:b9:60:a2:ea  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:19:d2:bc:3e:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4569 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1146528 (1.0 MB)  TX bytes:385465 (376.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1100 (1.0 KB)  TX bytes:1100 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:49:12:fc  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe49:12fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84190 (82.2 KB)  TX bytes:39583 (38.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-BC-3E-81-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Desktop ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:14:2a:d8:a4:35  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fed8:a435/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:172070 (168.0 KB)  TX bytes:27107 (26.4 KB)
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:49:12:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6126 (5.9 KB)  TX bytes:7547 (7.3 KB)
```

Laptop iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:16:B6:AA:74:5A   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=98/100  Signal level=-27 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11g  ESSID:"fishnet"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:16:B6:AA:74:5A   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Desktop iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

If I have to, I'll just buy a wireless card with Linux support, but since this USB adapter works on my Kubuntu laptop, I'm surprised it can't connect when plugged into the desktop. Some final notes: my home network uses WPA, and I'm having trouble with one other USB device (an ATI RF remote) that worked out-of-the-box on my laptop but not on the desktop, so perhaps it's a USB problem? Also as a final thought, is it possible updating the bios might help? It's an old motherboard that I bought on Ebay, so maybe something in the bios handles USB wrong?

Have you gone into the Konsole and checked dmesg?  There might be some info about the USB devices.

---

### Post by kwilliam on 2008-08-21
Sorry, I should have thought to post dmesg! Here's the one for my laptop, where it works. I've already reinstalled a few different operating systems on the desktop, so I can't get the desktop dmesg right now, but I'll try to get that later. Currently I've got a 64-bit version of Mythbuntu installed, which isn't having much better luck. (Probably because the 64-bit driver isn't happy.)

dmesg | tail for laptop (working):
(Note: eth1 is my laptop's built-in Intel wireless card)
```
[12369.068125] usb 5-5: new high speed USB device using ehci_hcd and address 7
[12371.226774] usb 5-5: configuration #1 chosen from 1 choice
[12369.291929] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[12369.458192] usb 5-5: reset high speed USB device using ehci_hcd and address 7
[12371.654584] ndiswrapper: driver net8187b (Realtek Semiconductor Corp.,06/25/2008,5.1135.0625.2008) loaded
[12373.208989] wlan0: ethernet device 00:14:d1:49:12:fc using NDIS driver: net8187b, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8187 Wireless LAN USB NIC                                     ', 0BDA:8189.F.conf
[12373.209040] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[12373.209090] usbcore: registered new interface driver ndiswrapper
[12541.740044] eth1: deauthenticate(reason=3)
[12545.230343] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230350] eth1: deauthenticated
[12545.230357] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230363] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230409] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230415] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230421] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230427] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230433] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230439] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230445] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230451] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230457] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230463] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230469] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230475] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230481] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230487] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230493] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.230500] eth1: authenticate with AP 00:16:b6:aa:74:5a
[12545.231409] eth1: RX deauthentication from 00:16:b6:aa:74:5a (reason=7)
[12545.234788] eth1: RX authentication from 00:16:b6:aa:74:5a (alg=0 transaction=2 status=0)
[12545.234794] eth1: authenticated
[12545.234798] eth1: associate with AP 00:16:b6:aa:74:5a
[12545.236414] eth1: invalid aid value 0; bits 15:14 not set
[12545.236421] eth1: RX AssocResp from 00:16:b6:aa:74:5a (capab=0x431 status=12 aid=0)
[12545.236425] eth1: AP denied association (code=12)
[12545.430982] eth1: associate with AP 00:16:b6:aa:74:5a
[12545.432482] eth1: invalid aid value 0; bits 15:14 not set
[12545.432489] eth1: RX AssocResp from 00:16:b6:aa:74:5a (capab=0x431 status=12 aid=0)
[12545.432493] eth1: AP denied association (code=12)
[12545.631858] eth1: associate with AP 00:16:b6:aa:74:5a
[12545.633289] eth1: invalid aid value 0; bits 15:14 not set
[12545.633297] eth1: RX AssocResp from 00:16:b6:aa:74:5a (capab=0x431 status=12 aid=0)
[12545.633301] eth1: AP denied association (code=12)
[12545.830744] eth1: association with AP 00:16:b6:aa:74:5a timed out
[12547.088931] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12547.799022] wlan0: duplicate address detected!
[12554.426440] wlan0: duplicate address detected!
[12560.889170] eth1: RX disassociation from 00:16:b6:aa:74:5a (reason=7)
[12560.889180] eth1: RX disassociation from 00:16:b6:aa:74:5a (reason=7)
[12560.889186] eth1: RX disassociation from 00:16:b6:aa:74:5a (reason=7)
```

dmesg | tail for desktop (can't connect):
[CODE]

---

