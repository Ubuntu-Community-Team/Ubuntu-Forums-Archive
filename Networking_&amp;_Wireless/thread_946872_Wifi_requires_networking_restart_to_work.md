---
title: "Wifi requires networking restart to work"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by soho on 2008-10-13
Hi,

I recently installed a mythbuntu 8.04 frontend on a Dell Latitute D810. Everything, including wifi, worked fine out of the box, but I was anoyed by the network manager prompting for a keyring password to get my WPA key. This was a problem since mythtv starts automatically at login, but requires a network connection to the backend to work.
To fix this I changed the wifi connection from roaming to my specific ssid with dhcp enabled. This worked fine, but after reboot I got the "default" avahi ip address. I tries to remove avahi, but the problem persisted.
However, running /etc/init.d/networking restart after boot gives me a valid working wifi, but I cannot make it start in during boot.

My /etc/network/interfaces:
------------------------------
auto lo
iface lo inet loopback

iface eth1 inet dhcp
   address 10.0.0.20
   netmask 255.255.255.0
   gateway 10.0.0.99
   wpa-psk *** hex key *** 
   wpa-driver wext
   wpa-key-mgmt WPA-PSK
   wpa-proto WPA
   wpa-ssid kannik


auto eth1

#iface eth0 inet dhcp
-------------------------

from syslog after boot:

-----------------------
Oct 13 16:29:08 medialap NetworkManager: <info>  starting... 
Oct 13 16:29:08 medialap kernel: [   38.426456] NET: Registered protocol family 10
Oct 13 16:29:08 medialap kernel: [   38.426855] lo: Disabled Privacy Extensions
Oct 13 16:29:08 medialap kernel: [   38.427480] ADDRCONF(NETDEV_UP): eth1: link is not ready
....
Oct 13 16:30:04 medialap dhclient: No DHCPOFFERS received.

-------------------

syslog after /etc/networking restart:

-------------------
Oct 13 16:36:52 medialap dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5766
Oct 13 16:36:52 medialap dhclient: killed old client process, removed PID file
Oct 13 16:36:52 medialap dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct 13 16:36:52 medialap dhclient: Copyright 2004-2007 Internet Systems Consortium.
Oct 13 16:36:52 medialap dhclient: All rights reserved.
Oct 13 16:36:52 medialap dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 13 16:36:52 medialap dhclient: 
Oct 13 16:36:52 medialap dhclient: Listening on LPF/eth1/00:13:ce:10:16:e2
Oct 13 16:36:52 medialap dhclient: Sending on   LPF/eth1/00:13:ce:10:16:e2
Oct 13 16:36:52 medialap dhclient: Sending on   Socket/fallback
Oct 13 16:36:53 medialap dhclient: DHCPRELEASE on eth1 to 10.0.0.99 port 67
Oct 13 16:36:53 medialap dhclient: send_packet: Network is unreachable
Oct 13 16:36:53 medialap dhclient: send_packet: please consult README file regarding broadcast address.
Oct 13 16:36:53 medialap kernel: [   66.716273] ADDRCONF(NETDEV_UP): eth1: link is not ready
Oct 13 16:36:53 medialap dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Oct 13 16:36:53 medialap dhclient: Internet Systems Consortium DHCP Client V3.0.6
Oct 13 16:36:53 medialap dhclient: Copyright 2004-2007 Internet Systems Consortium.
Oct 13 16:36:53 medialap dhclient: All rights reserved.
Oct 13 16:36:53 medialap dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 13 16:36:53 medialap dhclient: 
Oct 13 16:36:53 medialap kernel: [   66.763005] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct 13 16:36:53 medialap kernel: [   66.807162] ieee80211_crypt: registered algorithm 'CCMP'
Oct 13 16:36:53 medialap kernel: [   66.882363] padlock: VIA PadLock not detected.
Oct 13 16:36:53 medialap modprobe: WARNING: Error inserting padlock_aes (/lib/modules/2.6.24-19-generic/kernel/drivers/crypto/padlock-aes.ko): No such device 
Oct 13 16:36:54 medialap dhclient: Listening on LPF/eth1/00:13:ce:10:16:e2
Oct 13 16:36:54 medialap dhclient: Sending on   LPF/eth1/00:13:ce:10:16:e2
Oct 13 16:36:54 medialap dhclient: Sending on   Socket/fallback
Oct 13 16:36:57 medialap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Oct 13 16:36:57 medialap dhclient: DHCPOFFER of 10.0.0.107 from 10.0.0.99
Oct 13 16:36:57 medialap dhclient: DHCPREQUEST of 10.0.0.107 on eth1 to 255.255.255.255 port 67
Oct 13 16:36:57 medialap dhclient: DHCPNAK from 10.0.0.99
Oct 13 16:36:58 medialap dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Oct 13 16:36:58 medialap dhclient: DHCPOFFER of 10.0.0.107 from 10.0.0.99
Oct 13 16:36:58 medialap dhclient: DHCPREQUEST of 10.0.0.107 on eth1 to 255.255.255.255 port 67
etc...
---------

What is the explanation why /etc/init.d/networking requires a second run after boot before the wifi starts working?

---

