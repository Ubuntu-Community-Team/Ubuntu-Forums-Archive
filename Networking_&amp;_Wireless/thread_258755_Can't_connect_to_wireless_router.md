---
title: "Can't connect to wireless router"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by Culito on 2006-09-16
I just got this shiny new Belkin 54g wireless router from Wally World.  I have two computers in my house, one Windoze(wifeys) and another Linux(mine.) I'm writing on her comp right now, because I can't get my Linux box to connect to the router.  Of course hers did immediately...
So here's what I got...
iwconfig:
lo   no wireless extensions.

eth1 no wireless extensions.

wlan0 IEEE 802.11-DS  EESSID:"rfsclient"  Nickname:"rfsclient"
      Mode:Ad-Hoc  Frequency:2.412 Ghz  Cell: 02:0D:D2:60:55:04
      Bit Rate:2 Mb/s  Tx-power:18 dB/m
      Retry Min limit:8  RTS thr: off   Fragment thr: off
      Encryption key: off
      Link quality=0/92 Signal level=-100dBm Noise Level=-100dBm
      And some more stuff all equaling 0. (no copy and paste here!)
sit0  no wireless extensions.

/etc/network/interfaces:
(everything commented out except these: )

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-essid rfsclient

auto wlan0

Interesting note: when I comment out the wireless-essid line, the router shows up in network manager, but I can't connect, and the iwconfig output shows everything with no wireless extensions.

Any other info you geniuses need?
thanks,
-C

---

### Post by Culito on 2006-09-17
Anybody? Or am I missing something obvious?

---

### Post by Culito on 2006-09-18
So I strung out a network cable in the mean time, and I can connect, but it's freakin' SLOW!!  The windows comp on wireless is about 3x faster than my linux box wired in!  I tell ya, if it ain't one thing, it's the other.

---

### Post by Ubuntop on 2006-09-18
Do you still have wired nic on auto in interfaces?

Do you see any wifi networks with 'iwlist scan'?

'ifup wlan0' do anything for ya?

---

### Post by Culito on 2006-09-18
Hey, thanks for the post.

I did uncomment the settings for eth0 and eth1.  Still is very slow.

Here's some wireless stuff:

root@Culito:/home/cully# ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:0d:88:e5:55:04
Sending on   LPF/wlan0/00:0d:88:e5:55:04
Sending on   Socket/fallback

root@Culito:/home/cully# ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:0d:88:e5:55:04
Sending on   LPF/wlan0/00:0d:88:e5:55:04
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

root@Culito:/home/cully# iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:0C:2E:F6
                    ESSID:"RadioFreeSandifer"
                    Mode:Master
                    Encryption key:off
                    Channel:11
                    Quality:61/92  Signal level:-30 dBm  Noise level:-91 dBm

So it 'sees' my router - it's "RadioFreeSandifer".  But the router just won't give it a IP address, I guess.  The router's DHCP server is on...

---

