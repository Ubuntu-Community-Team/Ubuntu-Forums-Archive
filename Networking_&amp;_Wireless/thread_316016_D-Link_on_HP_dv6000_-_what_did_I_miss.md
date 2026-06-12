---
title: "D-Link on HP dv6000 - what did I miss?"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by hellgeist on 2006-12-10
Hello, this is my first post on the forums, so I will do my best to be clear.

I run Ubuntu Dapper 6.06 on an HP Pavillion dv6000 laptop. When I first installed, I was running the 386 kernel.. 
At that time (this was only a week ago) I bought a D-Link USB wifi card (WUA-1340), extracted drivers via wine, and followed one of the excellent ndiswrapper guides on this site. My wifi card came up, and I was rolling fine. 

A few days ago I did a new clean install using the 2.6.15-27-k7 kernel, so I could install the 9629 nvidia drivers without crashing, and then proceeded to ndiswrapper my D-Link again. Now it won't connect - it doesn't seem to be able to get an ip, and I cannot figure out why. 

When I run Admin->Networking, I can see the wlan0 adaptor, the wifi card blinks away happily, and all my settings seem to indicate that it *should* be ready to go. If I run wifi radar I can even see my wireless network, but it will not let me on. (note: I have this problem whether wifi radar is installed or not).

I have all my network settings correct as far as I can tell - settings are left to auto, wep is set to open, and the essid and wep keys are correct. I've read every guide I could find, and search the forum and google, and I am thinking that there is something I am missing. I am relatively new to linux issues like this, so any help would be greatly appreciated.

Here are some outputs:

ndiswrapper -v:
utils version: 1.7
driver version: 1.8

sudo iwlist wlan0 scanning: 
wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"Nightshade"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-48 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

netstat -rn: 
only shows data for eth0

sudo dhclient3 wlan0:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/xx:xx:xx:xx:xx:xx
Sending on   LPF/wlan0/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

sudo gedit /etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Nightshade
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
auto wlan0

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo gedit /etc/modprobe.d/ndiswrapper:
alias wlan0 ndiswrapper


Thank you for reading my post,

~H

---

### Post by midia on 2006-12-22
Hi there,

I don't know if this will help, but a few hours ago I posted my steps in getting my wua1340 to work here:

[LINK]("http://www.ubuntuforums.com/showthread.php?t=270756&highlight=wua+1340")

Maybe this will help you.

A couple of things.  

1)  With ndiswrapper, it seems to work best to first set your essid using iwconfig.  Using just admin>networking hoses my connectivity.  Once connected, I went to the networking program and enabled and set my essid.

2)  I noticed your protocol is 11b instead of 11g in:

sudo iwlist wlan0 scanning:
wlan0 Scan completed :
Cell 01 - Address:
...
ESSID:"Nightshade"
[COLOR="Red"]Protocol:IEEE 802.11b[/COLOR]

My iwlist wlan0 scanning shows 11g

wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:FE:8E:AA
                    ESSID:"my home network"
                    [COLOR="Red"]Protocol:IEEE 802.11g[/COLOR]
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-72 dBm  Noise level:-256 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

Don't know if that makes a difference.

Take care.

---

