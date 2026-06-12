---
title: "Setting ppp0 as default gateway."
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by jkndrkn on 2005-05-30
I have wlan0 and ppp0 connections. I can reach the internet with my wlan0 connection, but not with my ppp0 connection.

Here is my routing table when both are on:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.5.96.65      0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 wlan0

```

Here is my routing table when just ppp0 is on:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.5.96.65      0.0.0.0         255.255.255.255 UH        0 0          0 ppp0

```

Here is my routing table with just wlan0 on:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG        0 0          0 wlan0

```

I noted that the main differences are in the flags "U" vs "UH" and the lack of a "UG" entry for my ppp0.

I've tried using route add with my ppp0, but that doesn't seem to help. Is there a way to set up my ppp0 such that it will be used as a gateway when wlan0 is not connected? Thank you.

---

### Post by jkndrkn on 2005-06-01
Heh, seems that answering questions relating to 56k connections is fairly bothersome. Here are some answers I got at a different forum. Can someone verify and elaborate on these statements? Thanks!

[list]you need to add the default route for the ppp0 interface before it will forward packets to where they need to go.[/list] 

[list]Add "defaultroute" to your ppp configuration file.[/list]

---

