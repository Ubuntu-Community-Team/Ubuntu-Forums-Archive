---
title: "Wifi will not start after boot.."
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by l_ninjo on 2008-07-12
Hello,
on my laptop wifi will not automatically start. I've to restart network and everything seems fine. See the lsmod output befor and after networking restart. wlan_tkip is missing.What is the problem? What is the solution?

root@toshi:~# lsmod | grep wlan
wlan_scan_sta 14720 1
wlan 207728 4 wlan_scan_sta,ath_rate_sample,ath_pci

root@toshi:~# /etc/init.d/networking restart
* Reconfiguring network interfaces... There is already a pid file /var/run/dhclient.ath0.pid with pid 5598
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:e0:8a:cb:1e
Sending on LPF/ath0/00:19:e0:8a:cb:1e
Sending on Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:e0:8a:cb:1e
Sending on LPF/ath0/00:19:e0:8a:cb:1e
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPOFFER of 192.168.1.100 from 192.168.1.1
DHCPREQUEST of 192.168.1.100 on ath0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 42184 seconds.
root@toshi:~# lsmod | grep wlan
wlan_tkip 13696 2
wlan_scan_sta 14720 1
wlan 207728 5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci

---

### Post by prshah on 2008-07-12
> **l_ninjo said:**
> 

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801

DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11



Looks like you have some conflict with wifi0 and ath0. ath0 is correct and should be used; the wifi0 alias is incorrect and should not appear. Can you post the output of ```
cat /etc/network/interfaces
``` You should comment out lines related to wifi0 and enable automatic handling of ath0.

---

### Post by l_ninjo on 2008-07-13
I can not agree with you..... If there would be an faulty "interfaces" file, networking restart should not work. 
-----------------------------------------
root@toshi:~# cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface ath0 inet dhcp
wpa-psk ************************************************************
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid ddwrt

auto ath0
-----------------------------------
Meanwhile I put the networking restart in the rc.local. It's not fine but a workaround. Cheers l_ninjo

---

### Post by lisati on 2008-07-13
I've had the "unknown hardware address" message too, but since my networking works well enough most of the time, I haven't bothered researching it....

There is a note in one of the wireless tutorials about networking not starting after a system restart. One solution can be found here:
[http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---

