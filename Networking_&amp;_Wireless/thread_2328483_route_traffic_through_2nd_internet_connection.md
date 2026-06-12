---
title: "route traffic through 2nd internet connection"
date: 2016-06-21
forum: Networking &amp; Wireless
---

### Post by bizhat on 2016-06-21
I have 2 internet connections on my PC.

I removed gateway for one of the net connection, so other stay default and all traffic goes through it.

For using 2nd internet connection, i manually add routes with route command. I route all traffic to a remote server through 2nd network connection, then establish a ssh tunnel to that remote server, then configure fireofx to use that socks proxy (ssh tunnel).

```

boby@hon-pc-01:~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlxe8de270b3955
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s29f7u3
188.40.131.x   192.168.8.1     255.255.255.255 UGH   0      0        0 enp0s29f7u3
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlxe8de270b3955
192.168.8.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s29f7u3
boby@hon-pc-01:~ $ 

```

Is my current routing table, all traffic to remote server 188.40.131.x is routed via 2nd network interface "enp0s29f7u3".

Problem with this setup is it changes my IP to remote servers (ssh tunnel) IP and add some extra lags for some applications i use (java).

Is there anyway i can setup a local socks5 proxy, that route all incoming traffic to it via the 2nd network connection with out actually using a remote server ?

---

