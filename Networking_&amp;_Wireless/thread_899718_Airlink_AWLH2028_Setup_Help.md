---
title: "Airlink AWLH2028 Setup Help"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by kaxixi on 2008-08-24
[I]I have followed the instructions on the forum ([http://ubuntuforums.org/showthread.php?t=588279&page=2](http://ubuntuforums.org/showthread.php?t=588279&page=2)) for setting up wireless with ndiswrapper and the Win98 drivers provided on my Airlink's cd.

I think the computer detects the wireless card correctly and that ndiswrapper is using the correct driver:[/I]

erez@dabeast:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8185 (rev 20)
0000:00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6105M [Rhine-III] (rev 96)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

erez@dabeast:~$ sudo ndiswrapper -l
Installed ndis drivers:
net8185         driver present, hardware present

*However, when I attempt to load the driver (section 3.5 of [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)), the connection doesn't appear to work:*

erez@dabeast:~$ sudo depmod -a
erez@dabeast:~$ sudo modprobe ndiswrapper
erez@dabeast:~$ tail /var/log/messages
Aug 24 13:10:42 localhost gconfd (erez-4793): starting (version 2.14.0), pid 4793 user 'erez'
Aug 24 13:10:42 localhost gconfd (erez-4793): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0Aug 24 13:10:42 localhost gconfd (erez-4793): Resolved address "xml:readwrite:/home/erez/.gconf" to a writable configuration source at position 1
Aug 24 13:10:42 localhost gconfd (erez-4793): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 24 13:10:42 localhost gconfd (erez-4793): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3Aug 24 13:10:42 localhost gconfd (erez-4793): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 24 13:11:10 localhost kernel: [17180258.888000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Aug 24 13:11:27 localhost kernel: [17180276.580000] rtl8180: Bringing up iface
Aug 24 13:11:28 localhost kernel: [17180276.792000] rtl8180: Card successfully reset
Aug 24 13:11:28 localhost kernel: [17180277.720000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

*Same shows up when I run iwconfig:*

erez@dabeast:~$ iwconfig
lo        no wireless extensions.

wlan0     802.11b/g  ESSID:"Yoeli"
          Mode:Managed  Frequency=2.467 GHz  Access Point: Not-Associated
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

*I have blacklisted the drivers in /etc/modprobe.d/blacklist and rebooted (the file includes the following):*

# wireless network card driver
blacklist rtl8180
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

*But at some point, I've run dmesg and it still seems to be using the rtl8180 wireless driver*

erez@dabeast:~$ dmesg
...
[17180276.580000] rtl8180: Bringing up iface
[17180276.792000] rtl8180: Card successfully reset
[17180277.720000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

*Any ideas on how to proceed?  Thank you!!*

---

### Post by kaxixi on 2008-08-24
*Bump.  Ideas?  Thought I'd also share what happens when I run ifdown and ifup:*

erez@dabeast:~$ sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:40:f4:f8:69:2c
Sending on   LPF/wlan0/00:40:f4:f8:69:2c
Sending on   Socket/fallback
erez@dabeast:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:40:f4:f8:69:2c
Sending on   LPF/wlan0/00:40:f4:f8:69:2c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

*About ready to give up and get a wireless bridge, and simply connect to it with a wire.*

---

