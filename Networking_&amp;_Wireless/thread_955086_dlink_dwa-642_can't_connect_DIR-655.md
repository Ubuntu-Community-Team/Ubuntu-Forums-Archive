---
title: "dlink dwa-642 can't connect DIR-655"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Scribblah on 2008-10-21
I recently bought Dlink's DIR-655 Wireless N router and the DWA-642 pc card. I was hoping to take advantage of wireless N speeds but even if not, at least have a good wireless connection for my Dell 2650 with Hardy.

I followed instructions found in the forums and elsewhere to get the card working - and it is. I can connect to wireless networks I can see in the neighborhood that have no security. I want to enable WPA or WPA2 but had absolutely no luck making that work. As a troubleshooting technique I backed the router down to WEP - no luck. Then to no security and still no luck. I can see the SSID and the connection is strong - just can't connect.

What do you need to know to help me? I'm not an absolute newb - but pretty close.

---

### Post by pytheas22 on 2008-10-21
First, try using [wicd]("http://wicd.sourceforge.net") instead of Network Manager to connect.  A lot of people have better luck with wicd, especially with WPA/WEP.

Also, just to be clear: when you say that you connected with security disabled, does that mean that you were able to load web pages?  Or do you just mean that Network Manager said that you were connected?

Please also try connecting with security disabled, then post the output of the following commands:
```

lshw -C Network
ifconfig
sudo iwlist scan
lspci -nn
lsusb
uname -m
```

---

### Post by Scribblah on 2008-10-22
Thank you. I had tried WICD before but had no luck. Tried it again upon your suggestion and find same results. Doesn't find any wireless networks. However if I go into Network Connection wireless properties, I can see 10+ nearby wireless networks in the SSID dropdown list.

Yes, when using Network Manager and after selecting "roaming" those 10+ networks would appear and it would auto connect to one of them with no security. And yes, I could load pages, not just connect to the wap.  I assume you knew the results of all your commands would be long, long.. with apologies for this lengthy paste:

```
mark@homehardy:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:ba:ed:af
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.0.193 latency=80 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:11:52:e2:6b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,08/28/2006,6.0.1.75 latency=128 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
mark@homehardy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5b:ba:ed:af  
          inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:feba:edaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7951 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10214467 (9.7 MB)  TX bytes:1029331 (1005.2 KB)
          Interrupt:10 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:188436 (184.0 KB)  TX bytes:188436 (184.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:52:e2:6b  
          inet6 addr: fe80::21b:11ff:fe52:e26b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:411 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34823 (34.0 KB)  TX bytes:58286 (56.9 KB)
          Interrupt:10 Memory:28000000-28010000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:11:52:e2:6b  
          inet addr:169.254.6.211  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Memory:28000000-28010000 

mark@homehardy:~$ sudo iwlist scan
[sudo] password for mark: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:D3:BF:93
                    ESSID:"Mark Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-15 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:13:10:F1:0C:5E
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:16:B6:38:99:CA
                    ESSID:"PianoHome"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:F8:FA:E0:89
                    ESSID:"weihs"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:12:0E:89:64:8F
                    ESSID:"07FX09004368"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 06 - Address: 00:1E:8C:B3:AC:D5
                    ESSID:"yeagle"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 07 - Address: 00:18:39:86:19:60
                    ESSID:"Secure Wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:13:10:EA:87:7E
                    ESSID:"Susan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:E0:98:DA:C1:86
                    ESSID:"04B412732962"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 10 - Address: 00:18:F8:1B:2C:69
                    ESSID:"carissas"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 11 - Address: 00:1E:8C:0B:15:E3
                    ESSID:"truant"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 12 - Address: 00:A0:C5:F2:73:C3
                    ESSID:"Third Floor"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
mark@homehardy:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 05)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 Go] [10de:0112] (rev b2)
02:01.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
03:00.0 Network controller [0280]: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter [168c:0023] (rev 01)
mark@homehardy:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
mark@homehardy:~$ uname -m
i686
```

---

### Post by pytheas22 on 2008-10-23
hmmm, I was trying to help someone last week with the same chipset (Atheros AR5416) who also couldn't connect no matter what he tried, which was a little worrying because we never figured it out.

But first of all, you say that in wicd you can't see any networks to connect to.  This is probably because it's not configured to use the right interface.  In preferences you can specify which interface to use; make sure it's using wlan0.  Does that make a difference?

---

### Post by Scribblah on 2008-10-27
You got it! Thank you so much. Changing it to Wlan0 did indeed allow Wicd to see all the wireless networks. Then I had to change the driver from madwifi to wext. I think I had tried all sorts of combinations including ndiswrappers. I truly appreciate your time.

---

### Post by Scribblah on 2008-12-22
I'm circling back around on this thread b/c I finally decided to change the router to use G and N rather than B and G. When I do that, I loose the wireless connection. I've tried changing the wpa supplicant driver from wext to madwifi and ndiswrapper - no luck. 

The router is set at WPA2 with pre-shared key. On a separate issue I ran into problems with WICD after a recent update that was solved by changing from a passphrase to the preshared key ([link here]("http://ubuntuforums.org/showthread.php?t=1009651")). In WICD advanced settings I've tried both (wpa 1/2 passprhase, wpa 1/2 pre-shared key) with no luck.

I could settle on Wireless G but I bought this card and this router specifically after searching for what wireless N products to buy that work with linux so it'll be failure not to get it working.

---

### Post by pytheas22 on 2008-12-22
ndiswrapper may simply not support 11n mode, but I'm not positive.  If that's the case, you should be able to use 11n mode by driving your card with the ath9k or madwifi drivers instead of ndiswrapper, however.

But before we go through the trouble of installing new drivers from scratch, let's at least see if we can't get 11n to work under ndiswrapper.  Please answer these questions:

1. with the router in g/n mode, does your network appear at all in wicd, or is it just invisible?  What about in the output of 'sudo iwlist scan'?

2. if you can see your network, what happens when you try to connect?  Do you get an IP address or does the connection time out?

Also, are you on Ubuntu 8.04 or 8.10?

---

### Post by Scribblah on 2008-12-22
Perhaps moot now - unbelievably...but first I answer: 

1. with the router in g/n mode, does your network appear at all in wicd, or is it just invisible? What about in the output of 'sudo iwlist scan'?

Yep, I could see 'em all.

2. if you can see your network, what happens when you try to connect? Do you get an IP address or does the connection time out?

Little bar would run back and forth and I believe message in the task-bar below would note something about authorization. I could go into advanced settings on the pre-shared key and click the little box to ensure I had the key right - and I did. But it never worked.

3. Also, are you on Ubuntu 8.04 or 8.10?

I'm on 8.04

So now for the shocker (for me at least) - I've just connected with a patch cable of late and when I went back to check settings to answer your questions I noted that "wired" said "connect" and my wireless router said "disconnect" Can't believe it. It's up and running. I have no idea how/why which is too bad. 

I did notice when I ran iwlist that the protocol lists as IEEE 802.11g. But when I look at router settings it tells me this computer is connected in 802.11n mode (but only with 13 Mbps despite 100% signal strength (it's 1 foot away for now)). I could set the router to N only but windows work machine doesn't have an appropriate card. Hoping to have this one have the best connection possible. Maybe it does already.

Thanks for your help (again).

---

### Post by pytheas22 on 2008-12-22
Well, I'm glad to hear you can actually connect.
> 
I did notice when I ran iwlist that the protocol lists as IEEE 802.11g. But when I look at router settings it tells me this computer is connected in 802.11n mode (but only with 13 Mbps despite 100% signal strength (it's 1 foot away for now)). I could set the router to N only but windows work machine doesn't have an appropriate card. Hoping to have this one have the best connection possible. Maybe it does already.

Especially under ndiswrapper, you shouldn't trust the reporting of things like signal strength or connection rate.  Because ndiswrapper depends on closed-source Windows drivers with no public documentation, it often doesn't report a lot of things accurately, and the ndiswrapper developers never worried too much about that--they just wanted to make wireless cards work at a time when few had native Linux support.

The only way to really test your 11n speeds would be to share a file over the local network between two 11n machines and see how fast the transfer is (keeping in mind that there could be other limiting factors, of course...above all that you can't write to any normal hard drive as fast as 11n networks can transmit data, so you would want to be writing to a ramdisk or something instead).  Devising and instituting an accurate test may take some work, but if you're interested enough in this it would be worth it.

Also, as I mentioned, madwifi should be able to support 11n speeds on your card and should report signal strength, etc. accurately.  There's a nice script [here]("http://ubuntuforums.org/showthread.php?t=798485") for building the latest madwifi from source.  After installing it, you will want to use 'lshw -C Network' to ensure that your card is actually being driven by madwifi, not ndiswrapper.  If you want to go back to ndiswrapper later, you will probably need to blacklist the ath_pci module.  I'm happy to explain all this in greater detail if you feel compelled to give madwifi a try and can't figure it out on your own...

---

### Post by Scribblah on 2009-02-02
Aaaarrrgh. This darn thing is driving me a bit mad. After experiencing that odd turn around where it just started working, it stopped again, then started, then stopped. Basically about every 4th or 5th boot it works. When it's not working, there is no link light but there is plenty of activity and I can see my own network and others. Perhaps a service I can start/stop that will get the link light working w/o rebooting?

---

### Post by pytheas22 on 2009-02-02
I'm not sure why the behavior would be inconsistent like that.  Could you please post the output of the following commands, once while the card is working and another time when it's not:
```

dmesg | grep -e ndis -e wlan -e ath
lshw -C Network
sudo iwlist scan
ping -c 10 google.com
ifconfig
```

---

### Post by Scribblah on 2009-02-03
OK after 4 boots I got on and here's the output while connected... 

```
user@laptop:~$ sudo dmesg | grep -e ndis -e wlan -e ath
[   39.514483] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.754541] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
[   40.227203] ndiswrapper: using IRQ 10
[   40.438680] wlan0: ethernet device 00:1b:11:52:e2:6b using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
[   40.502764] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   40.505034] usbcore: registered new interface driver ndiswrapper
[  105.696313] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  114.880363] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  167.670784] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  223.984036] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  302.081790] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  305.015556] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  417.619924] wlan0: no IPv6 routers present
user@laptop:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:ba:ed:af
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=80 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:11:52:e2:6b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,08/28/2006,6.0.1.75 ip=192.168.0.188 latency=128 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
user@laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:F1:0C:5E
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:21:91:D3:BF:93
                    ESSID:"This is my router"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:21:29:97:A8:16
                    ESSID:"fatpads2008"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:1F:33:B4:55:A0
                    ESSID:"ritter"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:13:10:EA:87:7E
                    ESSID:"Susan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

user@laptop:~$ ping -c 10 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=243 time=188 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=243 time=144 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=243 time=160 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=243 time=150 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=243 time=120 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=6 ttl=243 time=120 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=7 ttl=243 time=134 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=8 ttl=243 time=125 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=9 ttl=243 time=125 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=10 ttl=243 time=125 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8999ms
rtt min/avg/max/mdev = 120.342/139.504/188.479/20.810 ms
user@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5b:ba:ed:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88028 (85.9 KB)  TX bytes:88028 (85.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:52:e2:6b  
          inet addr:192.168.0.188  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:fe52:e26b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:900610 (879.5 KB)  TX bytes:175623 (171.5 KB)
          Interrupt:10 Memory:28000000-28010000 

```

I changed the SSID of my router above to "This is my router." It is set to mixed mode accepting G and N, channel width: 20MHz, WISH: active, and security mode: WPA/WPA2 - Personal.

Wife needs to get on now so next time I'm on I'll repeat commands when it won't connect and then try to get back on to post - thanks as always for your amazing support.

---

### Post by Scribblah on 2009-02-26
Yikes what a slacker I am - wife's machine and it's been a busy time. OK here goes when it doesn't connect...

```
user@laptop:~$ sudo dmesg | grep -e ndis -e wlan -e ath
[sudo] password for xxxxxx: 
[   39.725438] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   40.045638] ndiswrapper: driver net5416 (,08/28/2006,6.0.1.75) loaded
[   40.516663] ndiswrapper: using IRQ 10
[   40.727895] wlan0: ethernet device 00:1b:11:52:e2:6b using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
[   40.790594] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   40.792987] usbcore: registered new interface driver ndiswrapper
[   99.392040] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  109.257990] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  436.368677] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  593.104474] wlan0: no IPv6 routers present
[  469.867385] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  470.032976] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  519.871245] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  572.471864] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  800.075271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1009.956906] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1065.327498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1117.970192] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1351.688392] ADDRCONF(NETDEV_UP): wlan0: link is not ready
user@laptop:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:ba:ed:af
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=80 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:11:52:e2:6b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,08/28/2006,6.0.1.75 latency=128 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
user@laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:29:97:A8:16
                    ESSID:"fatpads2008"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:18:3A:E0:B8:E1
                    ESSID:"08FX10102858"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:13:10:EA:87:7E
                    ESSID:"Susan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:13:10:F1:0C:5E
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:21:91:D3:BF:93
                    ESSID:"This is my router."
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:14:BF:28:46:40
                    ESSID:"home01"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:1E:2A:70:EE:1E
                    ESSID:"Network-V"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:3/100  Signal level:-94 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:1E:8C:B3:AC:D5
                    ESSID:"Yeagles"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 09 - Address: 00:E0:98:DD:D7:9D
                    ESSID:"05B401992271"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 10 - Address: 00:1F:33:B4:55:A0
                    ESSID:"ritter"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

user@laptop:~$ ping -c 10 google.com
ping: unknown host google.com
user@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5b:ba:ed:af  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148952 (145.4 KB)  TX bytes:148952 (145.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:52:e2:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113 (113.0 B)  TX bytes:225 (225.0 B)
          Interrupt:10 Memory:28000000-28010000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:11:52:e2:6b  
          inet addr:169.254.6.211  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Memory:28000000-28010000 
```

I notice a WICD update today which I'm going to apply despite the fact last time I did so, it [caused trouble]("http://ubuntuforums.org/showthread.php?t=1009651"). As always, thanks in advance for your time.

---

### Post by pytheas22 on 2009-02-26
hmmm, unfortunately there's no solid clue in the output you posted as to why it works sometimes but not other times.  I'm wondering however if simply reinserting the ndiswrapper module would solve the problem.  The next time you boot and are unable to connect, please run these commands:
```

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

Then wait a few seconds and try to connect again.  You can repeat this process a few times if it doesn't work on the first try.  Is this enough to get you connected?

---

### Post by Scribblah on 2009-02-27
OK. Will do. Remember that this is related to N configuration b/c if I set the router back to B/G it works fine. Also, if I attempt to connect to a neighbors B/G network the link light on the D-Link card stays solid where it does not when I try to connect to mine (doesn't light up except in about 1 of 4/5 boots. That's pre-authentication b/c I don't know the password for their network.

---

### Post by Scribblah on 2009-03-01
Defeated. That didn't work. Looked promising b/c after the second command the link light would come on and remain solid for while, but no connection made. Tried this numerous times and fiddled with various settings (preshared key vs. passphrase, etc.) but no luck.

Hopefully one day my investment in an N router and N nic will actually provide some benefit. For now, router moved back to G only and it connects every time w/o fail. Boooo.

Hey thanks again for all your help.

---

### Post by pytheas22 on 2009-03-01
Sorry you didn't figure out a better solution.  With any luck, the native drivers should support your card by the time Jaunty is released in April, and native drivers should do better with 11n than ndiswrapper.

---

### Post by Scribblah on 2009-03-05
Cool!  Didn't know that was coming. I'll try it out and post back results.

---

### Post by davoudi on 2010-03-21
I have tried everything this is what I have by now.

> [    1.552485] device-mapper: multipath: version 1.1.0 loaded
[    1.552488] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.387233] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.387244] ath9k 0000:02:00.0: setting latency timer to 64
[   22.436798] ath: EEPROM regdomain: 0x65
[   22.436801] ath: EEPROM indicates we should expect a direct regpair map
[   22.436805] ath: Country alpha2 being used: 00
[   22.436806] ath: Regpair used: 0x65
[   22.442886] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   22.443474] Registered led device: ath9k-phy0::radio
[   22.443496] Registered led device: ath9k-phy0::assoc
[   22.443522] Registered led device: ath9k-phy0::tx
[   22.443546] Registered led device: ath9k-phy0::rx
[   23.032012] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.345065] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[   37.345204] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[   37.350459] wlan0: direct probe responded
[   37.350462] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[   37.354811] wlan0: authenticated
[   37.354838] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[   37.358461] wlan0: RX AssocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=3)
[   37.358465] wlan0: associated
[   37.367723] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.618134] wlan0: no IPv6 routers present
[  144.554019] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
[  368.348860] wlan0: deauthenticated from 00:1c:f0:c0:97:29 (Reason: 6)
[  369.577073] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[  369.582658] wlan0: direct probe responded
[  369.582667] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[  369.584593] wlan0: authenticated
[  369.584632] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[  369.588375] wlan0: RX ReassocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=3)
[  369.588385] wlan0: associated
[  527.725788] wlan0: deauthenticated from 00:1c:f0:c0:97:29 (Reason: 6)
[  528.897120] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[  528.908028] wlan0: direct probe responded
[  528.908038] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[  528.911299] wlan0: authenticated
[  528.911325] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[  528.915392] wlan0: RX ReassocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=3)
[  528.915396] wlan0: associated
[  551.083134] wlan0: deauthenticated from 00:1c:f0:c0:97:29 (Reason: 6)
[  552.247315] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[  552.251947] wlan0: direct probe responded
[  552.251954] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[  552.254905] wlan0: authenticated
[  552.254930] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[  552.260754] wlan0: RX ReassocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=1)
[  552.260758] wlan0: associated
[  693.669589] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[  693.669710] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[  693.879527] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[  694.078412] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[  694.085158] wlan0: direct probe responded
[  694.085165] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[  694.087054] wlan0: authenticated
[  694.087080] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[  694.093053] wlan0: RX AssocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=1)
[  694.093058] wlan0: associated
[  938.804784] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020


---

### Post by pytheas22 on 2010-03-21
davoudi: first off, how close is your computer to your router?  Some of the error messages in your dmesg (in particularly, the "disassociating by local choice, reason=3" stuff) usually (but not always) have to do with being almost out of range.

A second, possibly unrelated problem is the error message:
```

ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020 
```

According to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040") this should have been fixed, but may not really have been.  Which version of Ubuntu are you using?  Have you applied all updates?

It may help to recompile your wireless drivers using the latest code from [http://linuxwireless.org;](http://linuxwireless.org;) if you need help with that, let me know and I'll post specific instructions.

---

### Post by davoudi on 2010-03-21
> **pytheas22 said:**
> davoudi: first off, how close is your computer to your router?  Some of the error messages in your dmesg (in particularly, the "disassociating by local choice, reason=3" stuff) usually (but not always) have to do with being almost out of range.

A second, possibly unrelated problem is the error message:
```

ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020 
```According to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407040") this should have been fixed, but may not really have been.  Which version of Ubuntu are you using?  Have you applied all updates?

It may help to recompile your wireless drivers using the latest code from [http://linuxwireless.org;](http://linuxwireless.org;) if you need help with that, let me know and I'll post specific instructions.

 Thanks for your reply. 

 I am running Ubuntu 9.10 on a Sony VAIO 14" Intel Core i3 330M (VPCCW23FDW). I am normally not 4 meters far from my router unless I am sleeping in other room!

 I am using D-Link so I first blacklisted a series of free drivers.

 I then updated my kernel for new drivers using last Karimc package update (linux-backports-modules-karmic). 

 I also installed the driver for wireless card ([https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)).

 Now I can browse internet with average speed and  listen to light streams (if wireless network is not interupted). But I still couldn't completely download my  income box from my Exchange 2007 email server. I am using Davmail which is not really very fast Gatway.

 I will try to read the post you proposed and I will happily ask for you help when I need. Thanks.

---

### Post by davoudi on 2010-03-21
Ok, so should I create my own kernel ([https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)) using the patch for AR93xx suuport to ath9k([http://bombadil.infradead.org/~mcgrof/tmp/ar93x-03-18-v2.patch]("http://bombadil.infradead.org/%7Emcgrof/tmp/ar93x-03-18-v2.patch"))? This sounds kinda serious ;) but I will give it a try.
[B]
[/B]

---

### Post by pytheas22 on 2010-03-21
Before going to the trouble of compiling a whole new kernel, I would try compiling just the wireless drivers using the most up-to-date development code (as opposed to the stable code that you already tried, which is not as up-to-date).

To compile and install the development drivers, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2."  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make ###this may take a few minutes; be patient
sudo make unload
sudo make load
sudo make install
```

If you get any errors, please post them.  Otherwise, reboot after this and see if you have any more luck with your wireless driver.  If it still doesn't work, please post the output of:
```

modinfo ath9k
dmesg | grep -e ath -e wlan
lspci -nn | grep -i atheros
```

If this still doesn't work, you could try ndiswrapper, although that would not be an ideal solution.

---

### Post by davoudi on 2010-03-22
> **pytheas22 said:**
> Before going to the trouble of compiling a whole new kernel, I would try compiling just the wireless drivers using the most up-to-date development code (as opposed to the stable code that you already tried, which is not as up-to-date).

To compile and install the development drivers, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2."  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make ###this may take a few minutes; be patient
sudo make unload
sudo make load
sudo make install
```If you get any errors, please post them.  Otherwise, reboot after this and see if you have any more luck with your wireless driver.  If it still doesn't work, please post the output of:
```

modinfo ath9k
dmesg | grep -e ath -e wlan
lspci -nn | grep -i atheros
```If this still doesn't work, you could try ndiswrapper, although that would not be an ideal solution.

 Yes, you completed my journey. Things seems much more stable by now. Is there anyway to check the performance of current setting? Now I see 4.32 Mb/s using a network speed check([http://www.speedtest.net/](http://www.speedtest.net/)).  But I don't feel that number when I am downloading things.

 By the way I didn't type sudo make unload in the last time I was installing the stable driver. Could that cause the problem?

 Now I can gradually focus in graphic driver.

---

### Post by pytheas22 on 2010-03-22
Glad to hear it's more stable now.  I don't know of any way in Ubuntu to check the wireless speed, other than download a file to see the download rate (for example, run wget from the terminal and it will tell you the download rate...but keep in mind that the bottleneck could be on the uploading server's end, not necessarily your wireless card's).

> 
By the way I didn't type sudo make unload in the last time I was installing the stable driver. Could that cause the problem?

No, that shouldn't have mattered, as long as you rebooted for the new drivers to take effect.

---

### Post by davoudi on 2010-03-23
> **pytheas22 said:**
> Glad to hear it's more stable now.  I don't know of any way in Ubuntu to check the wireless speed, other than download a file to see the download rate (for example, run wget from the terminal and it will tell you the download rate...but keep in mind that the bottleneck could be on the uploading server's end, not necessarily your wireless card's).



No, that shouldn't have mattered, as long as you rebooted for the new drivers to take effect.

 Under windows I get 22 Mb/s. The installation finished properly apart a few warnings.  These are output of commands you asked for.

 > 
$modinfo ath9k
filename:       /lib/modules/2.6.31-20-generic/updates/cw/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D2FCE033DD78D3AB11E320A
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        mac80211,led-class,ath,cfg80211
vermagic:       2.6.31-20-generic SMP mod_unload modversions 
parm:           debug:uint
parm:           nohwcrypt:Disable hardware encryption (int)


> 
$dmesg | grep -e ath -e wlan
[    1.541843] device-mapper: multipath: version 1.1.0 loaded
[    1.541846] device-mapper: multipath round-robin: version 1.0.0 loaded
[   21.942338] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.942350] ath9k 0000:02:00.0: setting latency timer to 64
[   21.991875] ath: EEPROM regdomain: 0x65
[   21.991877] ath: EEPROM indicates we should expect a direct regpair map
[   21.991881] ath: Country alpha2 being used: 00
[   21.991882] ath: Regpair used: 0x65
[   21.998078] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   21.998640] Registered led device: ath9k-phy0::radio
[   21.998653] Registered led device: ath9k-phy0::assoc
[   21.998672] Registered led device: ath9k-phy0::tx
[   21.998687] Registered led device: ath9k-phy0::rx
[   22.580801] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.287102] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[   34.287193] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[   34.292966] wlan0: direct probe responded
[   34.292971] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[   34.294879] wlan0: authenticated
[   34.294904] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[   34.298510] wlan0: RX AssocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=1)
[   34.298514] wlan0: associated
[   34.308020] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   44.769922] wlan0: no IPv6 routers present
[   80.253328] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[   80.253421] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[   85.031805] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[   85.229315] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[   85.233929] wlan0: direct probe responded
[   85.233942] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[   85.235828] wlan0: authenticated
[   85.235856] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[   85.239437] wlan0: RX AssocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=2)
[   85.239442] wlan0: associated
[  142.162679] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[  142.162777] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[  145.982954] wlan0: deauthenticating from 00:1c:f0:c0:97:29 by local choice (reason=3)
[  146.179699] wlan0: direct probe to AP 00:1c:f0:c0:97:29 (try 1)
[  146.184321] wlan0: direct probe responded
[  146.184327] wlan0: authenticate with AP 00:1c:f0:c0:97:29 (try 1)
[  146.186234] wlan0: authenticated
[  146.186262] wlan0: associate with AP 00:1c:f0:c0:97:29 (try 1)
[  146.189876] wlan0: RX AssocResp from 00:1c:f0:c0:97:29 (capab=0x421 status=0 aid=2)
[  146.189882] wlan0: associated


> 
$ lspci -nn | grep -i atheros
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)



---

### Post by pytheas22 on 2010-03-23
Unfortunately, I don't see anything in the output you posted that would explain why transfer rate would be slow.  It may simply be the case that the Linux driver is currently just not as fast as the Windows equivalent, and there's no real solution.

You could try using ndiswrapper, which would drive the device using the Windows driver, but I've never had luck getting any of the Atheros 9xxx wireless cards (which include yours) working with ndiswrapper.

Otherwise, as long as the connection is at least stable--even if it's not as fast as on Windows--your best bet might be to leave well enough alone and try to live with 4.32 Mb/s bandwidth (which is faster than my Internet connection at home anyway, although maybe you're lucky and have a decent ISP :)

---

### Post by davoudi on 2010-03-23
> **pytheas22 said:**
> Unfortunately, I don't see anything in the output you posted that would explain why transfer rate would be slow.  It may simply be the case that the Linux driver is currently just not as fast as the Windows equivalent, and there's no real solution.

You could try using ndiswrapper, which would drive the device using the Windows driver, but I've never had luck getting any of the Atheros 9xxx wireless cards (which include yours) working with ndiswrapper.

Otherwise, as long as the connection is at least stable--even if it's not as fast as on Windows--your best bet might be to leave well enough alone and try to live with 4.32 Mb/s bandwidth (which is faster than my Internet connection at home anyway, although maybe you're lucky and have a decent ISP :)

 Thanks a lots for your time and patience. I will keep updating the driver. I remember I have already tried ndiswrapper, and I don't think if I uninstall it yet. But anyway it didn't work. Is it possible that they conflict with each other.?

---

### Post by pytheas22 on 2010-03-24
> Thanks a lots for your time and patience. I will keep updating the driver. I remember I have already tried ndiswrapper, and I don't think if I uninstall it yet. But anyway it didn't work. Is it possible that they conflict with each other.?

Well, ndiswrapper and the native ath9k driver conflict with each other in the sense that you can't have them both *loaded* at the same time.  But you can have them installed on your system at the same time.  By default, Ubuntu will choose to use ath9k over ndiswrapper if both are present, so in order to switch to ndiswrapper, you would have to either: 1) uninstall ath9k; 2) blacklist ath9k by adding the line "blacklist ath9k" to your /etc/modprobe.d/blacklist.conf file; or 3) manually rmmod ath9k and modprobe ndiswrapper in its place.

But that all aside, as I said, I think ndiswrapper just doesn't work with your family of wireless cards, due to issues with ndiswrapper that there's no way around...

---

### Post by davoudi on 2010-03-25
So that seems to be a kernel problem rather than driver because the same issue does not exist on other Linux distributions.  I read here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460886](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460886) that a new package here [https://launchpad.net/~stefan-bader-canonical/+archive/karmic]("https://launchpad.net/%7Estefan-bader-canonical/+archive/karmic") or [https://launchpad.net/~guido-iodice/+archive/best-intel](https://launchpad.net/~guido-iodice/+archive/best-intel) could resolve the problem. Would you suggest that? I read about this patch somewhere too [http://bombadil.infradead.org/~mcgrof/tmp/ar93x-03-18-v2.patch]("http://bombadil.infradead.org/%7Emcgrof/tmp/ar93x-03-18-v2.patch").

---

### Post by pytheas22 on 2010-03-25
Those packages could help.  I'd give them a try if you're still not satisfied with the performance of the ath9k driver.

---

### Post by davoudi on 2010-03-27
Wah, she said 
[PHP]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-2.6.31
[/PHP]
after I said sudo apt-get install linux-backports-modules-2.6.31

I already included the repository using!

[PHP]sudo add-apt-repository ppa:stefan-bader-canonical/karmic[/PHP]

---

### Post by pytheas22 on 2010-03-27
Did you run "sudo apt-get update" after adding the repository?  What is the output of:

```
apt-cache search linux-backports-modules
```

The package name may be more specific than linux-backports-modules-2.6.31.  It's probably something like linux-backports-modules-2.6.31-xx.

---

### Post by davoudi on 2010-04-04
> **pytheas22 said:**
> Did you run "sudo apt-get update" after adding the repository?  What is the output of:

```
apt-cache search linux-backports-modules
```The package name may be more specific than linux-backports-modules-2.6.31.  It's probably something like linux-backports-modules-2.6.31-xx.
Thanks for the command. I finally find time to install the package today and at the end get the same speed. I am doing ok now. Thanks for your time.

---

### Post by davoudi on 2010-04-23
It seems that I screw up something. I just installed the latest wireless driver from [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and now the wireless is disabled! I uninstalled the latest version and then install the older one but I still can't have my wireless connection enable. Any help appreciated.

---

### Post by davoudi on 2010-04-24
```

 dmesg | grep -e ath -e wlan
[    1.521544] device-mapper: multipath: version 1.1.0 loaded
[    1.521547] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.356263] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.356274] ath9k 0000:02:00.0: setting latency timer to 64
[   22.405813] ath: EEPROM regdomain: 0x65
[   22.405816] ath: EEPROM indicates we should expect a direct regpair map
[   22.405819] ath: Country alpha2 being used: 00
[   22.405821] ath: Regpair used: 0x65
[   22.412213] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   22.412783] Registered led device: ath9k-phy0::radio
[   22.412796] Registered led device: ath9k-phy0::assoc
[   22.412808] Registered led device: ath9k-phy0::tx
[   22.412824] Registered led device: ath9k-phy0::rx

```

---

### Post by pytheas22 on 2010-04-24
> 
It seems that I screw up something. I just installed the latest wireless driver from [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and now the wireless is disabled! I uninstalled the latest version and then install the older one but I still can't have my wireless connection enable. Any help appreciated.

What do you mean by you can't enable your wireless?  Does NetworkManager fail to detect a wireless device?  Are you unable to scan for wireless networks?

What is the output of:
```

ifconfig
ifconfig -a
lshw -C Network
sudo iwlist scan
```

---

### Post by davoudi on 2010-04-24
The wireless connection was disabled after I installed latest driver. I can't enable it when I right click on the network manager icon (it appears gray).

> 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:be:b4:47:48  
          inet addr:24.83.34.17  Bcast:24.83.35.255  Mask:255.255.252.0
          inet6 addr: fe80::224:beff:feb4:4748/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2038486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:401033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1197282261 (1.1 GB)  TX bytes:31280582 (31.2 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5125441 (5.1 MB)  TX bytes:5125441 (5.1 MB)

> 
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:24:be:b4:47:48  
          inet addr:24.83.34.17  Bcast:24.83.35.255  Mask:255.255.252.0
          inet6 addr: fe80::224:beff:feb4:4748/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2045140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1199186162 (1.1 GB)  TX bytes:31355952 (31.3 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5125441 (5.1 MB)  TX bytes:5125441 (5.1 MB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 2c:81:58:ec:85:ab  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> 
lshw -C Network 
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 2c:81:58:ec:85:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:e7a00000-e7a0ffff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:24:be:b4:47:48
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=24.83.34.17 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:35 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


> 
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

vboxnet0  Interface doesn't support scanning.


---

### Post by pytheas22 on 2010-04-25
If you type:
```

sudo ifconfig wlan0 up
```

can you then enable the interface and connect?

---

### Post by davoudi on 2010-04-25
I have tired that already

> 
sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132


---

### Post by pytheas22 on 2010-04-25
That's strange.  What is the output of:
```

cat /etc/NetworkManager/nm-system-settings.conf 
cat /etc/interfaces
```

Also, take a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464559") from last fall.  For many people there, the error you're getting from "sudo ifconfig wlan0 up" is related to the wireless being turned off.  Are you sure the wireless card is turned on (it could be disabled either in BIOS or via a switch)?

There are also some other possible solutions there that you could try, for example the stuff involving rfkill, or just rebooting the computer entirely.

---

### Post by davoudi on 2010-04-26
> **pytheas22 said:**
> That's strange.  What is the output of:
```

cat /etc/NetworkManager/nm-system-settings.conf 
cat /etc/interfaces
```Also, take a look at this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/464559") from last fall.  For many people there, the error you're getting from "sudo ifconfig wlan0 up" is related to the wireless being turned off.  Are you sure the wireless card is turned on (it could be disabled either in BIOS or via a switch)?

There are also some other possible solutions there that you could try, for example the stuff involving rfkill, or just rebooting the computer entirely.

 Please accept my apology. Such a idiot I am. I have never noticed that little key.

---

### Post by pytheas22 on 2010-04-27
Ah, easy fix :)  Glad to hear it's solved.

---

### Post by davoudi on 2010-04-27
> **pytheas22 said:**
> Ah, easy fix :)  Glad to hear it's solved.
  I really feel ashamed. Thanks for your time.

---

