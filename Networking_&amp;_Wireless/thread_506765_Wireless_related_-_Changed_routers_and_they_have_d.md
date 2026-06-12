---
title: "Wireless related - Changed routers and they have different gateway addresses"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by Jongi on 2007-07-22
My old router to which my wireless card was connecting had IP address 192.168.1.1 (and this was the address in /etc/resolv.conf). My new router has IP address 10.0.0.2. I have changed the settings in /etc/wpa_supplicant.conf and /etc/network/interfaces.

Yet I get the following
```

root:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-down.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:6c:31:69:82
Sending on   LPF/wlan0/00:14:6c:31:69:82
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-post-down.d/wpasupplicant exited with return code 1
wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:14:6c:31:69:82
Sending on   LPF/wlan0/00:14:6c:31:69:82
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
```

I did a Ctrl-C at this point as it just loops.

```

root:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

##auto ppp0
##iface ppp0 inet ppp
##provider international

##auto ppp1
##iface ppp1 inet ppp
##provider local

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid SSID
wpa-ap-scan 1
wpa-proto TKIP
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxx
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
```

```

root:~# cat /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=1

network={
       ssid="SSID"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       #pairwise=CCMP TKIP
       #group=CCMP TKIP
       psk=750ce7778d28046b8d9ac7b8ba43ea853db4a34eeff8a0302b97745e61e4a9f3
```

---

