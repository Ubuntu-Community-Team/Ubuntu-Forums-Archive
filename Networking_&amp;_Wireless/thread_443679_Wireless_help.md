---
title: "Wireless help"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by robucf on 2007-05-14
I followed the sticky on wireless security but when I tried to restart networking I get the below:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5547
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:4d:66:fb:ed
Sending on   LPF/eth0/00:1a:4d:66:fb:ed
Sending on   Socket/fallback
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
wlan0: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
Segmentation fault (core dumped)
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:1a:4d:66:fb:ed
Sending on   LPF/eth0/00:1a:4d:66:fb:ed
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

Not sure where the errors are coming from, odd thing is I can connect to my neighbors router with no issues... just cannot connect to mine.

I have a TrendNet 443 (supported card), I see my wireless network with the scan command and as mentioned followed the sticky.

ifconfig
ath0      Link encap:Ethernet  HWaddr 00:18:E7:1B:46:5C
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:e7ff:fe1b:465c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2926268 (2.7 MiB)  TX bytes:525021 (512.7 KiB)

eth0      Link encap:Ethernet  HWaddr 00:1A:4D:66:FB:ED
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1528 (1.4 KiB)  TX bytes:1528 (1.4 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-18-E7-1B-46-5C-00-00-00-00-00-00-00-00-00                                                                 -00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24496 errors:0 dropped:0 overruns:0 frame:7595
          TX packets:4356 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:5475990 (5.2 MiB)  TX bytes:642635 (627.5 KiB)
          Interrupt:17

---

### Post by agurk on 2007-05-14
Could you please post the contents of your /etc/network/interfaces file?

---

### Post by robucf on 2007-05-14
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver madwifi
wpa-ssid myssid
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk my id as described

I am posting all of this while connected to my neighbor's wireless lan so I know the hardware is fine.  I just cannot connect to my wireless router.  In the router I have WPA2,AES+TKIP, do not broadcast SSID.

---

### Post by agurk on 2007-05-14
Hmm.. your wireless network interface is *ath0*, but you have written *wlan0* in your /etc/network/interfaces file.

---

### Post by robucf on 2007-05-14
I tried changing that I get a No DHCPOFFERS received.

---

### Post by agurk on 2007-05-14
Are you sure your router is set up to offer DHCP to wireless clients? Does it work if you set an address manually?

---

### Post by robucf on 2007-05-14
> **agurk said:**
> Are you sure your router is set up to offer DHCP to wireless clients? Does it work if you set an address manually?

Yes I have 3 other PC's working wireless-ly.

---

### Post by robucf on 2007-05-14
I got it to work, I changed it to TKIP and it worked =/

---

### Post by robucf on 2007-05-15
> **robucf said:**
> I got it to work, I changed it to TKIP and it worked =/

As is usually typical, I spoke too soon.  After a reboot, it no longer worked.  I had to manually restart the network 2 or 3 times for it to get an IP, ../network restart.  Is there a time out, number of retries, something I can set, or maybe I forgot to do something so it autostarts?  Any ideas?

---

