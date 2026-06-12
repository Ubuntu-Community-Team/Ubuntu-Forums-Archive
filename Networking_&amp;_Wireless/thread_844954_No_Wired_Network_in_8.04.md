---
title: "No Wired Network in 8.04"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by FrostedMouse on 2008-06-30
In Ubuntu and Kubuntu 8.04 the system will not accept a DNS address from the router.  This is strange because the system had/has no trouble in 7.10 on live cd's or full installs, yet 8.04 will not connect.

The router claims that it receives an IP request and sends an OFFER several times, but the system never seems to acknowledge that the offer was received.

Both versions (7.10 / 8.04) appear to be identifying the network car properly and using the same driver to set it up. I have tried manually entering DNS information to force the card to up and connect, which doesn't seem to work.  Any suggestions or assistance in this matter would be greatly appreciated.

My current install is ubuntu 8.04

---

### Post by FrostedMouse on 2008-06-30
Looking at several other posts, this seems to be the first step so.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1a:92:4a:e6:9a
          inet6 addr: fe80::21a:92ff:fe4a:e69a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:4848 (4.7 KB)
          Interrupt:245 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:1a:92:4a:f2:f6
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:246 Base address:0xc000

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:4a:e6:9a
          inet addr:169.254.8.183  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:245 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback
```

sudo /etc/init.d/networking restart 
```
 * Restarting Network    [OK]
```

---

### Post by FrostedMouse on 2008-07-18
No suggestions at all?  I atempted Using a USB ethernet adapter to update in an atempt to see if the problem had already been fixed in a patch, however this is not the case. Any help would be more than welcomed.

---

