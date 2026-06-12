---
title: "No WLAN with Linksys WPC54GS"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by christian8287 on 2005-11-03
Hi!

First my system configuration:
PC type: Gericom Masterpiece (512 MB RAM, ATI 9000 Mobility, 32 Bit)
Distribution: Ubuntu 5.10 "Breezy Badger"
Wireless PCMCIA Card: Linksys WPC54GS
Wireless Router: Linksys WRT54GS
PCIID: 14e4:4320 (rev 03)
ndiswrapper version: I installed it from source (version 1.5 stable)
Windows drivers: lsbcmnds.inf, bcmwl5.sys
Kernel version: 2.6.12-9-386

My problem:
ndiswrapper was installed correctly. The driver was also correctly installed (driver present, hardware present). There is also no problem in loading the ndiswrapper module. I am sitting two metres away from my access point (without any wall). I tried ifup wlan0, but I don't get any DHCPOFFER from the router. But when I call iwlist wlan0 scan, it finds my router with link quality of 0?? Configuring the network interfaces at startup takes a long time. If I try to set the essid with iwconfig I get no error message, but when I call iwconfig wlan0, the essid is not set.

Here is some output:

ifup wlan0:
```
root@RUDI:/home/christian# ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:66:c6:86:56
Sending on   LPF/wlan0/00:0f:66:c6:86:56
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

dmesg after modprobe ndiswrapper:
```
[4297237.551000] ndiswrapper version 1.5 loaded (preempt=no,smp=no)
[4297237.562000] ndiswrapper: driver lsbcmnds (Cisco-Linksys ,LLC.,02/19/2004, 3.50.21.11) loaded
[4297237.584000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4297237.592000] ndiswrapper: using irq 9
[4297238.729000] wlan0: vendor: ''
[4297238.729000] wlan0: ndiswrapper ethernet device 00:0f:66:c6:86:56 using driver lsbcmnds, 14E4:4320:1737:4320.5.conf
[4297238.731000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[4297249.601000] wlan0: no IPv6 routers present
```

iwconfig for wlan0:
```
root@RUDI:/home/christian# iwconfig wlan0
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map wlan0

iface wlan0 inet dhcp
wireless-essid linksys
auto wlan0
```

Scan of all AP:
```
root@RUDI:/home/christian# iwlist wlan0 scan
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:3B:C8:C2
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-36 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

If you need more information, pleas let me know.

Has anyone an idea, what I can do?

Thanks in advance!

regards,
Christian.

---

### Post by radupisano on 2006-03-15
Christian, 

I have a different problem with this. However, I can associate fine to the AP, this is how my /etc/network/interfaces file looks like:

```
auto wlan0
iface wlan0 inet dhcp
name Wireless LAN card
wireless_keymode open
wireless_essid   ESSID
wireless_key 212672C9DB    
wireless_channel 5
wireless_mode    auto
#wireless_nick KUBUNTU
#address 192.168.1.60
#netmask 255.255.255.0 
#network 192.168.1.0 
#broadcast 192.168.1.255 
#gateway 192.168.1.1 
# dns-* options are implemented by the resolvconf package, if installed
#dns-nameservers 192.168.1.1 

```

If you set the wireless_mode to auto, you should start seeing the AP, which is what fixed my problem. The problem that I have is that I know that the card is being associated with the AP, but it does not get an IP address for the life of it... It also does not work with a static IP either. To irritate me more, the KWiFiManager sees my AP with 100% strength but yet I cannot use it....

My card is a Linksys WPC54GS. I hope that this might help you in your problem, and I hope somebody else that sees this can help me out in how to fix this.

Thanks...

---

