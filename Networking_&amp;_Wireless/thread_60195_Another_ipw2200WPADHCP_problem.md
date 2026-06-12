---
title: "Another ipw2200/WPA/DHCP problem"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by oracel on 2005-08-26
Hi, I followed the how-to for ipw2200 and wpa. Everything seems to be working just fine, here's the output from iwconfig:
```
root@fiskebolle:/home/andreas # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"ParAvion"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0F:CB:AC:20:01
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=79/100  Signal level=-50 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

sit0      no wireless extensions.

``` 

However, when I try to retrieve an IP address from the dhcp server using dhclient, the following happens:
```
root@fiskebolle:/home/andreas # dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:e7:7d:37
Sending on   LPF/eth1/00:0e:35:e7:7d:37
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
...etc etc
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@fiskebolle:/home/andreas #

```

I haven't tried static ip. Issuing a dhclient on a normal ethernet interface works just fine, so there's nothing wrong with the server (I think). Here's the output from a successful dhclient:

```
root@fiskebolle:/home/andreas # dhclient eth0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0a:e4:a9:dc:27
Sending on   LPF/eth0/00:0a:e4:a9:dc:27
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.1
bound to 10.0.0.248 -- renewal in 1763 seconds.
root@fiskebolle:/home/andreas #

```

Any ideas?

---

### Post by luca_linux on 2005-08-27
Try to add or remove (according to what you've been trying untill now) the "-w" flag in the wpa_supplicant command.

If this doesn't work, try to disable wpa on both the AP and the client and see if it gets the IP with DHCP.

Then let me know.

---

### Post by briguy on 2005-09-10
I'm having the same trouble - my wireless worked almost flawlessly under Hoary.  Today I upgraded to Breezy, and I can't get an IP address for my ipw2200.  Here's my dhclient output:

```
root@laptop:/home/bw # dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 7514
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:0e:35:4e:b9:96
Sending on   LPF/eth0/00:0e:35:4e:b9:96
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.0.100
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```


iwconfig gives:
```

eth0      IEEE 802.11g  ESSID:"myessid"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:3A:6F:18:6D
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:my wep key   Security mode:open
          Power Management:off
          Link Quality=93/100  Signal level=-35 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1
```


The end result is that I can't set "Default gateway device" as eth0 even though the connection itself seems fine.  I checked the dhclient.pid files under /var/run/ , and while the eth1 files were full of IP address info, the eth0 files were empty, or just had a pid number.  Not sure if this info is useful or not, I just can't think of anything else to look at!

Thanks.

---

### Post by briguy on 2005-09-12
Okay, problem fixed.  All I had to do was comment out the map eth1 part of my /etc/network/interfaces.  Have a look:

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
#	map eth1

# The primary network interface
iface eth1 inet dhcp


iface eth0 inet dhcp
wireless-essid XXXXXXXXXXX
wireless-key XXXXXXXXXXXXXX

auto eth1

auto eth0

```

---

