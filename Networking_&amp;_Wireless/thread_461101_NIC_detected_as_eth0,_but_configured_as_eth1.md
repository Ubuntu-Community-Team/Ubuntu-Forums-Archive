---
title: "NIC detected as eth0, but configured as eth1"
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by gambit32 on 2007-06-01
Ive got an odd issue.  Just got some new hardware, and I moved my hard drive over from a different system.

It detects my NIC fine, as eth0.  But it then configures it under eth1.

**Here are the dmesg entries regarding the hardware:**
[   27.977388] eth0: ADMtek Comet rev 17 at Port 0xb800, 00:04:5A:83:74:4F, IRQ 3.
[   43.778231] eth1: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   51.198321] eth1: no IPv6 routers present


**ethtool doesnt see eth0 at all anymore**
gambit32@ubuntu:~$ ethtool -i eth0
Cannot get driver information: No such device

**eth1 is there though**
gambit32@ubuntu:~$ ethtool -i eth1
driver: tulip
version: 1.1.14
firmware-version:
bus-info: 0000:02:0b.0


**ifconfig configured it fine**
eth1      Link encap:Ethernet  HWaddr 00:04:5A:83:74:4F
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe83:744f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:670 errors:0 dropped:0 overruns:0 frame:0
          TX packets:791 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:56330 (55.0 KiB)  TX bytes:103413 (100.9 KiB)
          Interrupt:3 Base address:0xb800


**Theres no "comet" module loaded, but my "tulip" one is there:**
gambit32@ubuntu:~$ lsmod | grep comet
gambit32@ubuntu:~$ lsmod | grep tulip
tulip                  53536  0


Nothing else seems to be amiss, and its up on the network.  Id typically just leave it as it is, but with my luck something will happen down the line, I'll forget I did this or left it like this, and im afraid ill run into problems.

Any suggestions?

---

### Post by netztier on 2007-06-01
> **gambit32 said:**
> Ive got an odd issue.  Just got some new hardware, and I moved my hard drive over from a different system.

It detects my NIC fine, as eth0.  But it then configures it under eth1.
...
Any suggestions?

At least once a week on this forum: check **/etc/iftab** for wrong/stale ethX <-> MAC-address assignments, remove or correct them.
**Example:**
```
marc@blaze:~$ more /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0E:0C:D0:B4:D3 arp 1
eth2 mac 00:A0:C9:98:82:0E arp 1
eth3 mac 00:50:8B:07:E9:83 arp 1

```

best regards

Marc

---

### Post by gambit32 on 2007-06-01
That was it!

I've used slackware for over 10 years, and even the latest version doesnt use /etc/iftab.  I had no idea this existed

Thanks

---

