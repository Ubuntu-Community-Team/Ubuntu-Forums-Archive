---
title: "VPN routing problems?"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by hotsawdust on 2008-06-01
Using Hardy and having some trouble with my VPN connection. Tunnel comes up fine using pptp however I can't communicate with any devices on the other side of the tunnel. 

Here is the routing table once connected. External IP of the pix interface replaced with "remote.ip.addr"

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

remote.ip.addr   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         *               0.0.0.0         U     0      0        0 ppp0


The VPN assigns addresses in the 10.0.0.0 range so ppp0 may be assigned an address like 10.10.20.24. The network I am trying to reach uses the 192.168.42.0 address space. 

This tunnel works fine in a windows virtual machine on the same PC. Any ideas?

Thanks in advance.

---

### Post by cpcgm on 2008-10-19
Did you find a solution?

---

### Post by SteveONCSU on 2010-12-23
> **hotsawdust said:**
> Using Hardy and having some trouble with my VPN connection. Tunnel comes up fine using pptp however I can't communicate with any devices on the other side of the tunnel. 

Here is the routing table once connected. External IP of the pix interface replaced with "remote.ip.addr"

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

remote.ip.addr   192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         *               0.0.0.0         U     0      0        0 ppp0


The VPN assigns addresses in the 10.0.0.0 range so ppp0 may be assigned an address like 10.10.20.24. The network I am trying to reach uses the 192.168.42.0 address space. 

This tunnel works fine in a windows virtual machine on the same PC. Any ideas?

Thanks in advance.

I'm having the same problem and I've never been able to find a way to fix it.  I connect to my company's internal VPN, everything works great except for public stuff thats on the WAN. I've seen someone fix this on another computer but I've never fixed my own.  Anybody know how to fix?

---

