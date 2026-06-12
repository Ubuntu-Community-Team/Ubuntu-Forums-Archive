---
title: "Routing without NAT..."
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by Ventajou on 2005-08-27
Hi,

I have a server with a wireless adapter (wlan0) and a regular ethernet card (eth0).
wlan0 (static IP, 192.168.128.1) is connected to my wireless access point (192.168.128.254) which has a firewall and dhcp enabled for rest of the wireless lan.
eth0 (static IP 192.168.0.1) is running a dhcp for my wired lan. IP forwarding is enabled.

Both networks work just fine, dhcp clients get a correct IP on either side but the systems on the wired lan cannot reach the wlan nor the internet. Every other thread and howto I have found explain how to setup a NAT but since my network is already behind a NAT, I just would like to setup a plain, basic, static routing. Can someone help me?

---

### Post by cwaldbieser on 2005-08-27
[QUOTE=Ventajou]Hi,

I have a server with a wireless adapter (wlan0) and a regular ethernet card (eth0).
wlan0 (static IP, 192.168.128.1) is connected to my wireless access point (192.168.128.254) which has a firewall and dhcp enabled for rest of the wireless lan.
eth0 (static IP 192.168.0.1) is running a dhcp for my wired lan. IP forwarding is enabled.

Both networks work just fine, dhcp clients get a correct IP on either side but the systems on the wired lan cannot reach the wlan nor the internet. Every other thread and howto I have found explain how to setup a NAT but since my network is already behind a NAT, I just would like to setup a plain, basic, static routing. Can someone help me?[/QUOTE]
If I am reading this correctly, your server is acting as the router between the wireless and wired LANs, and you want to be able to route wireless traffic through this server to the wired LAN (where presumably there is a route to the Internet).

Do you have IP forwarding enabled on the server?  
```

$ cat /proc/sys/net/ipv4/ip_forward

``` 
0 = IP forwarding is OFF.
1 = IP forwarding is ON.

---

### Post by Ventajou on 2005-08-28
IP forwarding is enabled. Also the internet is available through the wireless. My routing table is currently as follows:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.128.254 255.255.255.255 UGH   0      0        0 wlan0
192.168.128.0   *               255.255.255.0   U     0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.128.254 0.0.0.0         UG    0      0        0 wlan0

```

I suppose all I have left to do is add a route each way from the lan to the wlan, but I just can't figure out what the parameters should be...

---

### Post by cwaldbieser on 2005-08-28
[QUOTE=Ventajou]IP forwarding is enabled. Also the internet is available through the wireless. My routing table is currently as follows:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.128.254 255.255.255.255 UGH   0      0        0 wlan0
192.168.128.0   *               255.255.255.0   U     0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.128.254 0.0.0.0         UG    0      0        0 wlan0

```

I suppose all I have left to do is add a route each way from the lan to the wlan, but I just can't figure out what the parameters should be...[/QUOTE]

Well, the routing table looks a little odd because you have two default routes.  You are really only supposed to have one default.

Let's see if I can understand your network:
Your LAN on the eth0 side is a 192.168.0.0/24 network. Looks like your LAN on the wlan0 side is a 192.168.128.0/24 network.  I am now guessing your wireless access point is your gateway to the Internet?

So, you should want your server routing table to look roughly like:
```

Dest                    Gateway                    Mask                    Iface
--------------------------------------------------------------------------------
192.168.0.0        *                                 255.255.255.0    eth0
192.168.128.0    *                                 255.255.255.0    wlan0
default                192.168.128.254        0.0.0.0               wlan0

```
That is almost what you have anyway, minus the extra default route.

Now the PCs on the LAN on the eth0 side should have entries like:
```

Dest                    Gateway                    Mask                    Iface
--------------------------------------------------------------------------------
192.168.0.0        *                                 255.255.255.0    eth0
192.168.128.0    192.168.0.1               255.255.255.0    eth0
default                192.168.0.1               0.0.0.0                eth0

```
This assumes each of those PCs has a single NIC called eth0.  Basically, anything destined for the 192.168.0.0/24 network can be accessed directly on the local ethernet.  Anything else goes to your server which will take over the routing from there.

If you have this set up, and it still doesn't seem to work, try doing a traceroute from one of the wired PCs to an Internet site and see where the trace stops.

---

### Post by Ventajou on 2005-08-29
It's working now! Thanks!

I fixed the route on my server as you advised, then realised I set the dhcp server to hand out 192.168.128.254 as a gateway on 192.168.0.0/24 which is why nothing would go out. Finally I had to make sure I set a static route on the wireless router going back to my wired lan.

Thanks again for the help!

---

