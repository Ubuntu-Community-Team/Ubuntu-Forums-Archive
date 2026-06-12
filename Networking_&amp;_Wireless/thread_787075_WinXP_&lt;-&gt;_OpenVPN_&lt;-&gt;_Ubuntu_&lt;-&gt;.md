---
title: "WinXP &lt;-&gt; OpenVPN &lt;-&gt; Ubuntu &lt;-&gt; Win2003 with MSSQL"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by dreamie on 2008-05-08
Hi!

I have a openvpn network in place. My computer (WinXP) connects to a Ubuntu server with OpenVPN (2.0.1) installed and running. What I want is to be able to connect from my computer to a Win2003 server running MSSQL server that is on the same LAN as the Ubuntu server.

The two networks has the following ip range 192.168.0.0/24 and 192.168.74.0/24

Ubuntu routing table:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.8.0.2        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```

The vpn-server also routes the local IP of the server so I can access it with it's LAN IP, i.e. from my XP-machine (192.168.74.103) i can access 192.168.0.7 (Ubuntu server). But I cannot access 192.168.0.4 (Win2003 Server).

I've tried enabling client-to-client but no luck there.

I believe I need to configure routing to the Win2003 server on the ubuntu server but I am not too familiar with this, and there is just too much information I don't know where to start.

Could someone please hint me here and possibly direct me where to find information/tutorials about this?

Thanks in advance!

 / Peter

OpenVPN config:
```

proto udp
dev tun
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

---

