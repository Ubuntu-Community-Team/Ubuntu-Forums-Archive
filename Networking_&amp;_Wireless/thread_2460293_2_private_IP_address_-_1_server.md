---
title: "2 private IP address - 1 server ???"
date: 2021-04-06
forum: Networking &amp; Wireless
---

### Post by Frank P on 2021-04-06
I have a  local Ubuntu server - 20.04LTS, with one NIC
Logging in via SSH today I noticed, for the first time, the login screen is showing 2 addresses for the same NIC IPv4 for eno1 192.168.1.89 & 192.168.104
I can login in via either address 
Everything is okay but I'm curious as to whats going on :-)
Thanks
Frank

---

### Post by TheFu on 2021-04-06
Are you running any virtual machines or linux containers?  
Did you install any of those tools?

---

### Post by Frank P on 2021-04-06
Nope, no virtual machines. Haven't installed any containers or anything except what I get from apt update

---

### Post by Frank P on 2021-04-07
kind of weird -
The server has a static ip 192.168.1.89 confirmed by ifconfig
The static IP doesn't show in th Asus Routers table. The router shows the 192.168.1.104 IP
Server can be accessed by either

This seems to have happened when I updated from 18.04LTS  to 20.04LTS
The server is using Netplan and I didn't manually change it from network

---

### Post by TheFu on 2021-04-07
Less descriptions, more commands and output.

```
ifconfig
route -n
```
for a start.  Those might not be installed, so we may be stuck using the inferior commands:
```
ip a
ip route | column -t
```

---

### Post by Frank P on 2021-04-07
ifconfig

```

eno1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.89  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d6ae:52ff:feb8:a7ec  prefixlen 64  scopeid 0x20<link>
        ether d4:ae:52:b8:a7:ec  txqueuelen 1000  (Ethernet)
        RX packets 2139692  bytes 1228086361 (1.2 GB)
        RX errors 0  dropped 539775  overruns 0  frame 0
        TX packets 2381018  bytes 2732118132 (2.7 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3874  bytes 1476702 (1.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3874  bytes 1476702 (1.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```
route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eno1
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eno1
192.168.1.1     0.0.0.0         255.255.255.255 UH    100    0        0 eno1



```

---

### Post by TheFu on 2021-04-07
I don't see 2 IPs, do you?
I do see a screwed routing table, however. It looks like a VPN was activated, then shutdown, but the routing table wasn't cleaned up.
The expected routing table should be:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      10       0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eno1
```

The first line is the default route for internet traffic.
The second line is for LAN traffic.

---

### Post by Frank P on 2021-04-07
TheFu;14030724]I don't see 2 IPs, do you?

nope, don't see 2 IPs now - should have  relooked.

TheFu;14030724]I don't see 2 IPs, do you?
I do see a screwed routing table, however. It looks like a VPN was activated, then shutdown, but the routing table wasn't cleaned up.
The expected routing table should be:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      10       0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eno1
```

The first line is the default route for internet traffic.
The second line is for LAN traffic.[/QUOTE]

Have never tried to set up a VPN on this server. So don't know where that came from
The router still shows the 192.168.1.104 IP and not the static 192.168.1.89
The ubuntu logon still shows 2 IPs.
I'll try to get a screen shot to post later.

---

### Post by Frank P on 2021-04-07
here's a screen shot of the login - I hope :-)
Let me know if I didn't attach it properly

---

### Post by TheFu on 2021-04-07
That screen looks like for a router, not ubuntu.  The facts of networking come from the ip a and ip route commands.

---

### Post by Frank P on 2021-04-07
that screen shot comes from a Dell factory installed ubuntu 18.04LTS Desktop, updated via standard update process to 20.04LTS desktop, via an ssh login

---

### Post by Frank P on 2021-04-07
I hooked up a monitor to the server and that's exactly the same screen as I got form the ssh login

---

### Post by TheFu on 2021-04-07
> The facts of networking come from the ip a and ip route commands.  .

---

