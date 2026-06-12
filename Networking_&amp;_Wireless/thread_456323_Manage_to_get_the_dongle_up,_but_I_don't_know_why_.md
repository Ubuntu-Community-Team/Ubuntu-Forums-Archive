---
title: "Manage to get the dongle up, but I don't know why my wireless is still not working"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by TotallyConfused on 2007-05-27
I have an rt73 Edimax USB dongle, which I managed to successfully install after following the instructions here: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

However, I still cannot use the wireless to surf the net! I ran sudo dhclient wlan0 and the following is the output I got

```
aaron@aaron-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5607
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0e:2e:c7:e6:28
Sending on   LPF/wlan0/00:0e:2e:c7:e6:28
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.1.5
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

The output for iwconfig is as follows:

```
aaron@aaron-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"homenetwork"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Am I missing out something here? My brother can use the wireless of his windows-based machine to connect to the router, so I don't think the router is the problem. I really need some ideas here.:confused:

---

### Post by handaxe on 2007-05-27
These probably apply (note the driver is the issue not the make of the device):

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108264](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108264)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86980](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86980)

The solution seems to be to install serialmonkey drivers, tho' they do not support SMP (latest CVS offers SMP support!)  and PREEMPT:  [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) also:  [http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)  in Italian. And the following offers config method   [http://ubuntuforums.org/showthread.php?t=434952](http://ubuntuforums.org/showthread.php?t=434952)

HA

---

