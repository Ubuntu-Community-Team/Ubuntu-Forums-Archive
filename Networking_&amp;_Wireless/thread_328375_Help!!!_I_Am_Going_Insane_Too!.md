---
title: "Help!!! I Am Going Insane Too!"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by peloreus on 2006-12-30
Singing the linux wireless card blues, could use some help.

ifconfig
wlan0 802.11b ESSID:"Linksys"
Mode:Managed Frequency:2.432 GHz Access Point: Not-Associated
Bit Rate=11 Mb/s
Retryn Fragment thrff
Power Managementff
Link Quality:30/100 Signal level:-38 dBm Noise level:-186 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
iwconfig
wlan0 Link encap:Ethernet HWaddr 00:0F:66:3B:94:E3
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:1460 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:636 (636.0 b) TX bytes:56940 (55.6 KiB)
Interrupt:9 Memory:d2830000-d2830100



peloreus@peloreus:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4736
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:66:3b:94:e3
Sending on LPF/wlan0/00:0f:66:3b:94:e3
Sending on Socket/fallback
peloreus@peloreus:~$ user@ubuntu:~$ sudo ifup wlan0
bash: user@ubuntu:~$: command not found
peloreus@peloreus:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:66:3b:94:e3
Sending on LPF/wlan0/00:0f:66:3b:94:e3
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

peloreus@peloreus:~$ netstat -rn
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

the ethernet is conflicting? WEP codes are disabled on my router. WifiDocs/Device/Broadcom BCM4311 rev 01 (ndiswrapper) tutorial tells me to remove MAC identifier, but I don't know how to comment/remove line. I am experiencing despair.

peloreus@peloreus:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

---

