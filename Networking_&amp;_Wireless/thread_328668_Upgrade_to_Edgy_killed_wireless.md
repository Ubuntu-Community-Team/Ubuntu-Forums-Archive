---
title: "Upgrade to Edgy killed wireless"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by frost_ireland on 2006-12-31
Hi,
My first post here, and my first week with Linux.  I  started with Edubuntu 6.16 LTS a week or so ago, was having great fun with it, about the only problem I had to solve was getting wireless WPA encryption working, which i did, but to be honest I can't remember exactly how! 

Just upgraded to Edgy this morning (no significant problems) and now my wireless AP isn't being detected any more.  I'm using my wired connection at the moment.  

This is a dell inspiron 8600 centrino laptop with intel pro wireless2200 bg

Based on other posts, I've listed below output from several commands which might help diagnose this.  I'm a software developer  but a Linux noob; I'm willing to figure stuff out but any pointers would be a great help!

Thanks!

**iwlist eth1 scanning:**
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)


**iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"maybe just a salad"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:20:F1:6E  
          inet addr:192.168.1.33  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1833031 (1.7 MiB)  TX bytes:323092 (315.5 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:4E:78:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:7 Base address:0xc000 Memory:faffc000-faffcfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5304 (5.1 KiB)  TX bytes:5304 (5.1 KiB)


**route:**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth0

**iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:CC:2D:55:0C
                    ESSID:"maybe just a salad"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=83/100  Signal level=-47 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 840ms ago

**/etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
#	network 192.168.1.0
#	broadcast 192.168.1.255
#	# dns-* options are implemented by the resolvconf package, if installed
#	dns-nameservers 192.168.1.1
#
#iface eth1 inet dhcp
#wireless-essid maybe just a salad
#wireless-key s:mypasswordwashere
#
#auto eth1

iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp
wireless-essid maybe just a salad
wireless-key s:mypasswordwashere

auto eth1

---

### Post by n00b@linux on 2006-12-31
It looks like your access point is using WPA-PSK but your /etc/network/interfaces file is set up for WEP.  To set up WPA-PSK take a look at the thread in my sig or read the sticky in this forum.

---

### Post by TheWizzard on 2006-12-31
> **n00b@linux said:**
> It looks like your access point is using WPA-PSK but your /etc/network/interfaces file is set up for WEP.  To set up WPA-PSK take a look at the thread in my sig or read the sticky in this forum.
indeed

a few tips:
- ESSID:"maybe just a salad" -> don't use spaces in names. 
- always make installation notes. 
- always backup /etc. comparing a configuration file with one that used to work helps a lot.

---

### Post by frost_ireland on 2006-12-31
thanks for your suggestions, i'll try it again, taking notes this time (new year's resolution!) and see how it goes...

---

### Post by frost_ireland on 2007-01-02
working on WEP (haven't bothered with WPA):

turned off encryption
changed ssid so it had no spaces
disabled wired connection
killed network manager 
got connection
added WEP
restarted all networking
got connection.

haven't gone further (WPA) but am happy for now.  

thanks for help on this thread and in the general forum community (i did a lot of searching).
it is a great support for those of us just getting used to the linux way of doing things

---

### Post by TheWizzard on 2007-01-04
> **frost_ireland said:**
> working on WEP (haven't bothered with WPA):

turned off encryption
changed ssid so it had no spaces
disabled wired connection
killed network manager 
got connection
added WEP
restarted all networking
got connection.

haven't gone further (WPA) but am happy for now.  

thanks for help on this thread and in the general forum community (i did a lot of searching).
it is a great support for those of us just getting used to the linux way of doing things

8)  enjoy ubuntu

---

