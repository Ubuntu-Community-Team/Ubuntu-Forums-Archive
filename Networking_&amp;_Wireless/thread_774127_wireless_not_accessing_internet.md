---
title: "wireless not accessing internet"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by stefanoBelletti on 2008-04-29
I feel really stupid.
I've just installed ubuntu 8.04
I have a router, an "eth0" and a "wlan0" (usb conceptronic 54, detected as atheros by lsusb)

routing thru eth0 i can surf the internet
routing thru wlan0 i cannot even ping the router (192.168.0.1)

the various  kwifimanager, RutilT show wlan0 connected to my wireless network.

probably is not a ubuntu problem, but it's me doing something really stupid :-(

can someone help me ?
thankyou !!!
<code>
------------------------------------------------------------------------------------------
iwconfig:
cb@ubuntu:~$ sudo ifup eth0
cb@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MIARETE"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1B:2F:43:24:5A
          Bit Rate=24 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Link Quality=70/100  Signal level=-56 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
----------------------------------------------------------------------------------------------
etc/network/interfaces:
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface wlan0 inet static
address 192.168.0.2
netmask 255.255.255.0
wireless-essid MIARETE
gateway 192.168.0.1
wireless-key s:644F7C151A
wireless-channel 5
auto wlan0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
----------------------------------------------------------------------------------------------
route-n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 wlan0
--------------------------------------------------------------------------------------------------
</code>

---

### Post by helgman on 2008-04-29
I've had similar problems. Might be the routes in your routing table. If the routes for eth0 is still there when you try to use the wlan0 connection this might fail since the system still tries to communicate via eth0.

I'm not sure if I have to delete routes or add them ... but the routing table is usually a problem when I switch from wired to wireless.

Regards,
Helgman

---

### Post by stefanoBelletti on 2008-04-29
thank you Halgman, i too suspect a problem with routes.
i'll try booting with "etc/network/interfaces" without eth0

---

