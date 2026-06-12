---
title: "Dell Inspiron 9300 / Ubuntu 7.04 - not connected to internet"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by Robert Leithe on 2007-10-03
I switched my laptop off yesterday afternoon. Ever since I can't get connected to the internet. The computer receives an IP-address, though. The computer I'm currently writing on is connected to the same 3Com switch and has received an address from the same pool.

I also had problems turning the Dell on since yesterday. This morning, on the first two attempts after entering my name and password I received the "standard latte" background but also a small white square in the top left corner of my screen. Upon moving the mouse pointer over this white square, the pointer changed shape to the I-bar (normally seen when you point to a text field). The computer was otherwise unresponsive, except I could hit the power-button and it would shut down. On my third attempt I chose Recovery Mode, and at the prompt for root password (or press Ctrl+D to continue) I pressed Ctrl+D and the system logged on seemingly normally. Except for the internet that is.

Any idea as to what I can check to get this running normally again?

EDIT1: Just remember that, upon shutting down yesterday evening (in a small cycle of starting up/shutting down) I saw a small mention that Firstarter had failed to start. But this is just a GUI, right, so this shouldn't have anything to do with this?

Also, although the Dell receives an IP it doesn't connect well with other machines in my network either, not just the internet.

EDIT3: As it turns out, I don't receive any response when pinging internally (10.0.0.*), but I do receive a response when pinging a public IP...

EDIT2:
Here are the results of a few commands I tried:
```
robert@C-3PO:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth1
```

```
robert@C-3PO:~$ cat /etc/resolv.conf 
search lan
nameserver 10.0.0.1
```

```
robert@C-3PO:~$ egrep -i '(error|fail)' /var/log/messages
Oct  2 20:57:24 C-3PO kernel: [216912.204000] RPC: failed to contact portmap (errno -5).
Oct  2 21:06:02 C-3PO kernel: [    3.468000] ahci: probe of 0000:00:1f.2 failed with error -22
Oct  2 21:07:34 C-3PO kernel: [  117.176000]  <6>sd 3:0:0:0: scsi: Device offlined - not ready after error recovery
Oct  2 21:07:34 C-3PO kernel: [  117.176000] sd 3:0:0:0: SCSI error: return code = 0x00010000
Oct  2 21:07:34 C-3PO kernel: [  117.176000] end_request: I/O error, dev sdc, sector 0
Oct  2 21:17:44 C-3PO kernel: [  727.132000] RPC: failed to contact portmap (errno -5).
Oct  2 23:05:52 C-3PO kernel: [    3.472000] ahci: probe of 0000:00:1f.2 failed with error -22
Oct  2 23:13:00 C-3PO kernel: [  453.776000] RPC: failed to contact portmap (errno -5).
Oct  3 06:48:59 C-3PO kernel: [    3.468000] ahci: probe of 0000:00:1f.2 failed with error -22
Oct  3 06:49:07 C-3PO kernel: [   34.992000] portmap: RPC call returned error 1
Oct  3 06:49:07 C-3PO kernel: [   34.992000] RPC: failed to contact portmap (errno -1).
Oct  3 06:49:07 C-3PO kernel: [   34.992000] portmap: RPC call returned error 1
Oct  3 06:49:07 C-3PO kernel: [   34.992000] RPC: failed to contact portmap (errno -1).
Oct  3 06:49:07 C-3PO kernel: [   34.992000] portmap: RPC call returned error 1
Oct  3 06:49:07 C-3PO kernel: [   34.992000] RPC: failed to contact portmap (errno -1).
Oct  3 06:49:07 C-3PO kernel: [   35.092000] portmap: RPC call returned error 1
Oct  3 06:49:07 C-3PO kernel: [   35.092000] RPC: failed to contact portmap (errno -1).
Oct  3 06:49:07 C-3PO kernel: [   35.092000] portmap: RPC call returned error 1
Oct  3 06:49:07 C-3PO kernel: [   35.092000] RPC: failed to contact portmap (errno -1).
Oct  3 06:49:07 C-3PO kernel: [   35.092000] lockd_up: makesock failed, error=-1
Oct  3 06:49:07 C-3PO kernel: [   35.092000] portmap: RPC call returned error 1
Oct  3 06:49:07 C-3PO kernel: [   35.092000] RPC: failed to contact portmap (errno -1).
Oct  3 06:49:07 C-3PO kernel: [   35.092000] portmap: RPC call returned error 1
Oct  3 06:49:07 C-3PO kernel: [   35.092000] RPC: failed to contact portmap (errno -1).
Oct  3 06:54:40 C-3PO kernel: [    3.528000] ahci: probe of 0000:00:1f.2 failed with error -22
Oct  3 06:54:48 C-3PO kernel: [   34.596000] portmap: RPC call returned error 1
Oct  3 06:54:48 C-3PO kernel: [   34.596000] RPC: failed to contact portmap (errno -1).
Oct  3 06:54:48 C-3PO kernel: [   34.596000] portmap: RPC call returned error 1
Oct  3 06:54:48 C-3PO kernel: [   34.596000] RPC: failed to contact portmap (errno -1).
Oct  3 06:54:48 C-3PO kernel: [   34.600000] portmap: RPC call returned error 1
Oct  3 06:54:48 C-3PO kernel: [   34.600000] RPC: failed to contact portmap (errno -1).
Oct  3 06:54:48 C-3PO kernel: [   34.672000] portmap: RPC call returned error 1
Oct  3 06:54:48 C-3PO kernel: [   34.672000] RPC: failed to contact portmap (errno -1).
Oct  3 06:54:48 C-3PO kernel: [   34.672000] portmap: RPC call returned error 1
Oct  3 06:54:48 C-3PO kernel: [   34.672000] RPC: failed to contact portmap (errno -1).
Oct  3 06:54:48 C-3PO kernel: [   34.672000] lockd_up: makesock failed, error=-1
Oct  3 06:54:48 C-3PO kernel: [   34.672000] portmap: RPC call returned error 1
Oct  3 06:54:48 C-3PO kernel: [   34.672000] RPC: failed to contact portmap (errno -1).
Oct  3 06:54:48 C-3PO kernel: [   34.672000] portmap: RPC call returned error 1
Oct  3 06:54:48 C-3PO kernel: [   34.672000] RPC: failed to contact portmap (errno -1).
Oct  3 07:00:02 C-3PO kernel: [    2.444000] ahci: probe of 0000:00:1f.2 failed with error -22
```

```
robert@C-3PO:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                                                                                   There is already a pid file /var/run/dhclient.eth0.pid with pid 5232
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:3f:df:5a:1a
Sending on   LPF/eth0/00:12:3f:df:5a:1a
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.0.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5942
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:24:90:52
Sending on   LPF/eth1/00:13:ce:24:90:52
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:3f:df:5a:1a
Sending on   LPF/eth0/00:12:3f:df:5a:1a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 10.0.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.0.1
bound to 10.0.0.8 -- renewal in 3083 seconds.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:24:90:52
Sending on   LPF/eth1/00:13:ce:24:90:52
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

Sincerely
Robert Leithe

---

### Post by noob12 on 2007-10-04
Do things improve if you run the following command

```
sudo ifconfig eth1 down
```

Can you post the output of these commands?

```

lspci -nn

sudo lshw -C network

ifconfig -a

route -n

cat /etc/network/interfaces

```

---

