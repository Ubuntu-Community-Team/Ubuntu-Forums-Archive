---
title: "Internet access"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by raaah on 2007-02-13
I desperately need help with this... I've been trying to sort out i/net access for a week now. Basically, I'm using a dual-boot XP Pro desktop with DHCP enabled WPA-PSK keyed router as one of three users.

Before I was using Kubuntu, but decided it wasn't for me and installed Ubuntu 6.10 (edgy).
I have no access to the net whatsoever. I want to use wireless, but I plugged an ethernet cable directly into the router and found no connection so I can't download patches/files from linux in any way (wireless works fine in xp though).

On kubuntu i felt i was getting close, I managed to use ndiswrapper and install a driver, though I think I may have a natively supported card (the Belkin F5D7000). In Ubuntu, ndiswrapper comes up with all sorts of errors when trying to install.

I don't know where to start. Here's the contents of iwconfig, ifconfig and /etc/network/interfaces. The latter is worryingly blank...

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          
sit0      no wireless extensions.

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:04:4B:01:1C:FA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:04:4B:01:1C:F9  
          inet6 addr: fe80::204:4bff:fe01:1cf9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25380 (24.7 KiB)  TX bytes:25380 (24.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:DD:A6:D6  
          inet6 addr: fe80::211:50ff:fedd:a6d6/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:11376 (11.1 KiB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-DD-A6-D6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

/etc/network/interfaces:

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

Any help would be greatly appreciated, thanks.

---

### Post by mikewhatever on 2007-02-13
Here are several links I'd try:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by Floppyjoe on 2007-02-13
If you are not using network-manager applet to connect to the network you will need to set up WPA encryption on your system. Here is a URL for help with that. Go down to the part where it says WPA Supplicant and continue from there.

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

Hope this helps,
Floppyjoe

---

