---
title: "Trying to connect to another computer on my network"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by unclejames on 2008-01-05
A rather odd problem that hopefully I can get some help with.

I have a wired ADSL router on 192.168.0.1. There's my Mac Mini over there, and that's 192.168.0.7, connected straight into the router using a wire.

Upstairs, also connected via a wire, is 192.168.10.1 - my (Fon) wireless router, which provides wireless throughout the house.

When running Windows XP, I connect to the wireless router's private signal and use DHCP. I can connect to my Mac Mini no problem, and can also 'see' my wired ADSL router.

When running Ubuntu, on the same box, I connect to the wireless router's private signal and use DHCP. However, I cannot 'see' either my Mac Mini or my wired ADSL router. Trying to 'ping' my Mac Mini results in no connection at all. But here I am on the internet, so I can see the rest of the world just fine - but not the machine over there.

Is that fixable? I've no idea about this stuff really...

Two (hopefully) useful bits of info below.

```

eth1      Link encap:Ethernet  HWaddr [snip] 
          inet addr:192.168.10.145  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::212[snip]:effe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

```

james@ubuntu:~$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

---

### Post by unclejames on 2008-01-12
Can anyone help with this? I suspect it's something to do with the netmask, but I'm too thick to understand how to fix it.

---

### Post by unclejames on 2008-01-12
(Bizarrely, it's now working. Who knows. Anyway. Panic over!)

---

