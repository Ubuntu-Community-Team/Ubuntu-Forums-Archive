---
title: "VPN routing problem after hardy upgrade"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by weller on 2008-04-28
Hi!
I used to connect to a server at work via pptp and gnome-network-manager under gutsy.
It worked but I had to do a
sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev ppp0
after the connection was established.

Now - after the hardy upgrade it doesn't work any more.

Please help me with fixing my routing problem.

Without VPN connection:
eth0 is my WIFI adapter and 192.168.1.1 (dd-wrt) the default gateway to the internet.
```
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.93.0    *               255.255.255.0   U     0      0        0 vmnet8
172.16.157.0    *               255.255.255.0   U     0      0        0 vmnet1
default         DD-WRT          0.0.0.0         UG    0      0        0 eth0

```

After connecting the VPN the routing table changes to
```
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
[provider IP] DD-WRT          255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.93.0    *               255.255.255.0   U     0      0        0 vmnet8
172.16.157.0    *               255.255.255.0   U     0      0        0 vmnet1
default         DD-WRT          0.0.0.0         UG    0      0        0 eth0

```

My local LAN and the destination LAN share the same IP range. Local 192.168.1.1 is the internet router and remote the same adress is a (file) server.


Thank you and
best regards,
  Andreas Weller

---

### Post by netztier on 2008-04-29
> **weller said:**
> Hi!
I used to connect to a server at work via pptp and gnome-network-manager under gutsy.
It worked but I had to do a
sudo route add -net 192.168.1.0 netmask 255.255.255.0 dev ppp0
after the connection was established. 

Will adding the routes to the network-manager vpn plugin configuration (via gconf-editor) help? See [ vpnc blocks internet access]("http://ubuntuforums.org/showthread.php?t=342546")

> **weller said:**
> 
My local LAN and the destination LAN share the same IP range. Local 192.168.1.1 is the internet router and remote the same adress is a (file) server.


This calls for an advanced NAT solution if you want to use both LANs simultaneously. 

Or consider changing one of the LAN's IP addressing. Problems like this are the precise reason why I always change the common default LAN address schemes away from 192.168.1.x, 192.168.0.x and the likes.

regards

Marc

---

