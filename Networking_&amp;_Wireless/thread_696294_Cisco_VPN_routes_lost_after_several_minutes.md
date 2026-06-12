---
title: "Cisco VPN routes lost after several minutes"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by macmilla on 2008-02-13
I'm having a problem with Cisco VPN client v.4.8 on Gutsy. I am able to connect successfully and everything works great.  After several minutes (somewhere between 2 and 20) I am unable to reach any destinations (host unreachable).  I am still connected to VPN.  I have to disconnect, then reconnect, then the process repeats.

The VPN client works on Windows on the same machine.  The linux VPN client works on a Fedora-based build provided by my company.  So I do not believe it is my laptop hardware, or anything on the server side.

Any ideas?  I tried VPNC, but no luck even connecting with that.  Any and all help would be really appreciated.

---

### Post by macmilla on 2008-02-14
Updating with more info.  

When I run the route command before connecting I get the following:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
192.168.167.0   *               255.255.255.0   U     0      0        0 vmnet8
192.168.57.0    *               255.255.255.0   U     0      0        0 vmnet1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
```

After initially connecting to via the cisco VPN client I get the following:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<hostname of company server> 192.168.2.1     255.255.255.255 UGH   0      0        0 eth0
141.144.0.0     *               255.255.0.0     U     0      0        0 cipsec0
default         dhcp-amer-rmdc- 0.0.0.0         UG    0      0        0 cipsec0
```

And after several minutes (3 to 20 or so, it varies), the route tables changes to the following:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
<ip address of company vpn server>  192.168.2.1     255.255.255.255 UGH   0      0        0 eth0
141.144.0.0     *               255.255.0.0     U     0      0        0 cipsec0
default         141.144.114.209 0.0.0.0         UG    0      0        0 cipsec0
```

Any ideas on what is causing the table to be modified?  Once it changes, I no longer can connect to anything (everything is host unreachable).  Any thoughts or suggestions?

---

### Post by macmilla on 2008-02-18
I seemed to have resolved my issue.  It was in fact DNS related.  My resolv.conf was being overwritten during my VPN connection by my router, causing me to lose my VPN DNS entries.  I installed the resolvconf package and that seemed to prevent the incorrect DNS entries from being re-inserted into my resolv.conf file.

---

