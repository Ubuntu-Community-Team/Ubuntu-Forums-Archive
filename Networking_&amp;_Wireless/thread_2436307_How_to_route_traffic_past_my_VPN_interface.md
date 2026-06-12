---
title: "How to route traffic past my VPN interface?"
date: 2020-02-04
forum: Networking &amp; Wireless
---

### Post by dwater on 2020-02-04
I normally work with my VPN enabled, but the server is located a long way away and I want to get access to an http/ftp server that is located close to my local network - it has some large files I need to access.

How can I route traffic past the VPN interface specifically for that one host?

I tried something like this:

$ sudo route add -host localserver.com dev ethernetif

where localserver.com is the server near my local network, and ethernetif is the physical ethernet connection, as shown on the output of 'netstat -rn'. I tried 'gw 192.168.1.1' too, which is the default gateway (w/o vpn), and the IP address of the server rather than the hostname (seems the same when the vpn is connected and when it isn't).

I used to do this sort of thing all the time, but not recently and I guess I forgotten something; or perhaps the vpn s/w is being even more clever than before (iinm, it's just OpenVPN).

Any ideas?

Ubuntu 19.10

---

### Post by SeijiSensei on 2020-02-04
Your traffic may be being masqueraded through the VPN so that routing alone won't solve the problem.  Please run these commands and post the output inside [noparse]```

```[/noparse] tags.

```

sudo iptables -t nat -L -nv
sudo iptables -L -nv

```

---

### Post by TheFu on 2020-02-04
Not all VPNs allow this "split tunnel" capability.  No company where I've worked did. The setting is controlled by the VPN server and cannot be modified on the client-side.

However, most commercial VPNs used by home users typically using openvpn routinely setup routing to allow the local /24 to be accessed directly. For example:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.88.11.5      128.0.0.0       UG    0      0        0 tun0
default         rt1             0.0.0.0         UG    0      0        0 enx000ec6c76418
10.88.11.1      10.88.11.5      255.255.255.255 UGH   0      0        0 tun0
10.88.11.5      *               255.255.255.255 UH    0      0        0 tun0
10.175.168.0    *               255.255.255.0   U     0      0        0 lxdbr0
104.200.153.89  rt1             255.255.255.255 UGH   0      0        0 enx000ec6c76418
128.0.0.0       10.88.11.5      128.0.0.0       UG    0      0        0 tun0
link-local      *               255.255.0.0     U     1000   0        0 enx000ec6c76418
**172.22.22.0     *               255.255.255.0   U     0      0        0 enx000ec6c76418**
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
```

Ignore the 10.175.168.0 and 192.168.122.0 , those are for containers and VMs here.

---

