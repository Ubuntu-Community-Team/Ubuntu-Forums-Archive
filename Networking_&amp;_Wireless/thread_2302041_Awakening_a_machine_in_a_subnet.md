---
title: "Awakening a machine in a subnet"
date: 2015-11-07
forum: Networking &amp; Wireless
---

### Post by User-007 on 2015-11-07
Hi all,

My configuration:
-DSL router with LAN
-LAN&WLAN router connected to DSL router

I have connected my HTPC to LAN&WLAN router  for easier access for both devices´ config. "Awakening" machine is connected straight to the DSL router.

However, WOL attempts fail in that setup (WOL works great if my HTPC is connected straight to the DSL router).

Anybody succeeded with that?
User JB

---

### Post by tgalati4 on 2015-11-07
Can the wake machine ping the HTPC?  [WoL]("https://help.ubuntu.com/community/WakeOnLan") is tricky.  Some routers have WoL built-in. Have you looked at the advanced settings of both routers?  Because WoL uses hardware addressing, it's possible there is a MAC filter between the routers that is causing WoL to fail.

---

### Post by User-007 on 2015-11-07
> **tgalati4 said:**
> Can the wake machine ping the HTPC?  [WoL]("https://help.ubuntu.com/community/WakeOnLan") is tricky.  Some routers have WoL built-in. Have you looked at the advanced settings of both routers?  Because WoL uses hardware addressing, it's possible there is a MAC filter between the routers that is causing WoL to fail.

I tried to ping the HTPC from wake machine, no success. Advanced settings do not mention about WOL or MAC Filtering (except of WLAN settings) in either setups.

---

### Post by tgalati4 on 2015-11-07
No ping means you don't have a route to your HTPC.  From both machines post:

```
netstat -r
```

---

### Post by User-007 on 2015-11-08
> **tgalati4 said:**
> No ping means you don't have a route to your HTPC.  From both machines post:

```
netstat -r
```

The output of the HTPC machine is

```

$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         zyxel.com       0.0.0.0         UG        0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0

```

Cannot repeat this step in wake machine since it is a Windows Phone 8.1 mobile..

User JB

---

### Post by tgalati4 on 2015-11-08
Try a different wake machine like a Linux laptop.  I don't have a Windows phone, so I can't help with that.

Your gateway should be the address of your router, not your internet provider (zyxel.com), otherwise, you can't get an internal route on your LAN.

Mine looks like:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
192.168.1.0     *               255.255.255.0   U         0 0          0 wlan0

192.168.1.1 is the address of the router that is connected to a DSL modem.  If you have a DSL router with ports, then use the internal address as the gateway.

---

### Post by User-007 on 2015-11-08
Hi, 

Just remembered that I have connected another HTPC to the DSL router.

Ran "netstat -r" for that (can be used as a wake machine, too):

```

$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         kotiboksi.Elisa 0.0.0.0         UG        0 0          0 eth0
192.168.100.0   *               255.255.255.0   U         0 0          0 eth0

```

But
```

wakeonlan [MAC)
Sending magic packet to 255.255.255.255:9 with [MAC]

```

No success from that machine, either.

What ping commands should I actually use? Originally tried ```
ping 192.168.1.0
``` from the WP8.1. But what is weird, ```
ping 192.168.100.0
``` also fails from same WP8.1. They both still are in a same subnetwork.

I am quite new with network protocols so please be patient.. :)

---

### Post by tgalati4 on 2015-11-08
Post /etc/network/interfaces and /etc/NetworkManager/NetworkManager.conf

---

### Post by User-007 on 2015-11-09
> **tgalati4 said:**
> Post /etc/network/interfaces and /etc/NetworkManager/NetworkManager.conf

I assume u now mean the awakened machine, the information is below:

/etc/network/interfaces:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
	up ethtool -s eth0 wol g

```


/etc/NetworkManager/NetworkManager.conf:
```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

```

---

### Post by tgalati4 on 2015-11-09
They look OK.  You need to change your gateway entries.  They should be a numeric IP address of your internal router.

---

### Post by User-007 on 2015-11-11
The config of my DSL router is very basic and thus I cannot set any gateway entries there. I gave up, but you actually solved the problem. I remembered I can use another HTPC to setup the WLAN router (it is connected to it). So I switched the LAN wire of the said HTPC (original question) from the WLAN router to the DSL router. WOL works perfectly, as earlier said.

Thanks a lot, tgalati4!

---

