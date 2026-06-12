---
title: "OpenVPN Routing"
date: 2013-11-26
forum: Networking &amp; Wireless
---

### Post by brandon-bilbo on 2013-11-26
Heres my setup:

<vpn client> -- <internet> --  <ubuntu server (2 nics)> --  <rest of LAN (192.168.0.0)>

From the client I can access everything on the server and the rest of the LAN as I wish.. everything seems to work from that end. But from the server I cannot even ping the client. Traceroute returns a bunch of lines with *.. I think it might have something to do with my routing table although it looks correct to me, but that doesn't say much...

Heres my routing table (ubuntu server):
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         98.196.114.1    0.0.0.0         UG        0 0          0 WAN
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
98.196.114.0    0.0.0.0         255.255.254.0   U         0 0          0 WAN
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 LAN

```

and heres my openvpn config
```



port 1194
proto udp
dev tun
ca ca.crt
cert provizon.org.crt
key provizon.org.key  # This file should be kept secret
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.0.0 255.255.255.0"
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3

```

All input is appreciated. Thanks.

---

### Post by SeijiSensei on 2013-11-26
The machine at 10.8.0.2 needs a gateway for 192.168.0.0/24.

Usually I add static routes by executing a script with the "up" directive rather than "push."  That script would look like

```

#!/bin/bash
/sbin/ip route add 192.168.0.0/24 via 10.8.0.1

```

if this runs on the machine with 10.8.0.2.  After marking the script executable I usually put it in the same directory as the OpenVPN conf files.  Call it /etc/openvpn/start_routes.

Using this method, openvpn.conf or its equivalent includes a line that reads:

```

[...]
up /etc/openvpn/start_routes
[...]

```

The server with multiple NICs needs to have forwarding enabled in /etc/sysctl.conf, but it sounds like you have taken care of that already.

---

