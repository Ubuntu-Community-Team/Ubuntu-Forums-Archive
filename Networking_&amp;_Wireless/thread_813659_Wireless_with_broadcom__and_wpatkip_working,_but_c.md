---
title: "Wireless with broadcom  and wpa/tkip working, but can't ping"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by mohnkern on 2008-05-31
This is a weird one.

I've got a notebook machine with one wireless card, and one standard network jack.

I got wireless working, it's connecting to my 802.11G network with WPA -TKIP.  (Don't ask, I kind of stumbled on a bunch of different articles and merged ideas).

I can get to web sites, DNS is working, etc.

However, when I try to ping any other machine on the network, or connect to web servers that are running on them, it's not connecting.

I'm at a bit of a lost to figure out why, I can't even ping the router I got an IP address from.

If I plug in the standard network cable, it works just fine, pinging works, etc.

Any ideas?

---

### Post by mohnkern on 2008-05-31
Well, I thought I was on a correct path.  I rebooted, and now when I run wifi-radar and click on connect, it goes through DHCPD discover several times, tells me no lease is available, and I'm not connected.

---

### Post by mohnkern on 2008-05-31
Here's what I used as core instructions:

[http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+hardy](http://ubuntuforums.org/showthread.php?t=760568&highlight=broadcom+hardy)

I also installed wifi-radar.

Here's the contents of /etc/wpa_supplicant.conf

p_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid="ESSID_IN_QUOTES"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="ASCII PSK Password in Quotes"
pairwise=TKIP
group=TKIP
}

and the results of wifi-radar

root@mohnkern-laptop:/etc# wifi-radar
dhclient3 --version 2>&1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:7e:8e:a9:35
Sending on   LPF/wlan0/00:19:7e:8e:a9:35
Listening on LPF/eth0/00:16:d3:5a:d2:47
Sending on   LPF/eth0/00:16:d3:5a:d2:47
Sending on   Socket/fallback
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:19:7e:8e:a9:35
Sending on   LPF/wlan0/00:19:7e:8e:a9:35
Listening on LPF/eth0/00:16:d3:5a:d2:47
Sending on   LPF/eth0/00:16:d3:5a:d2:47
Sending on   Socket/fallback
Stale pid file.  Removing
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Unsupported driver '-P'.

Listening on LPF/wlan0/00:19:7e:8e:a9:35
Sending on   LPF/wlan0/00:19:7e:8e:a9:35
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
Unable to obtain a lease on first try.  Exiting.

---

### Post by mohnkern on 2008-05-31
Wel, it's a bit confusing.  Wifi-radar is showing a number of local networks, including mine, so it's talking to the broadcom card, I know I've got the right network key.  It's WPA-TKIP and I think (but am not sure) that's right.  

However it still can't get an ip address from the router.

---

### Post by mohnkern on 2008-06-01
From bad to worse,  I reinstalled Ubuntu 32 bit, did a system update and ran the instructions at [http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy)


It can see the card, but when I try to run wpa_gui I get:

[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy)
 
Also Gnome's network manager doesn't see any networks.  

I'm really open to any suggestions.

---

