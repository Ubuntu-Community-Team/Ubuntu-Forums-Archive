---
title: "help: wireless connection was working, now its not"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by stevecrozz on 2007-01-02
RESOLVED: The problem was not with Ubuntu, or the laptop, or the WAP, my problem was with the linksys router which decided for whatever reason to stop issuing IP addresses.

So I had UBUNTU running nicely, but I wanted to start all over because I had made a bunch of changes I didn't need to make. So after reinstalling ubuntu 6.10 from the CD, I attempted to connect to my wireless network, which if I remember right worked perfectly the first time before the reinstall.

Now it has some problem that I can't find. I can't ping the gateway I use and certainly can't ping the outside internet. Here's my iwconfig:

EDIT: I also can't ping the WAP54G.

lo          no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"crosby"
             Mode:Managed  Frequency:2.437 Ghz  Access Point:  00:12:17:60:B5:5A
             Bit Rate:54 Mb/s     Tx-Power: 15 dBm
             Retry limit:15   RTS thr:off    Fragment thr:off
             Power Management:off
             Link Quality=77/100  Signal level=-58 dBm  Noise level=-59 dBm
             Rx invvalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:57  Missed beacon:0

sit0       no wireless extensions

---

### Post by jamesstansell on 2007-01-02
The "Access Point:" section is promising, although it doesn't guarantee a connection.  What does "ifconfig eth1" show?

What do these commands show? ```
sudo ifdown eth1
sudo ifup eth1
```

**Update**: OK, I see the original problem is resolved.  I'll leave these questions in case they can help someone with the same or similar problem.

---

### Post by stevecrozz on 2007-01-02
Just wanted to say thanks for your comment even though I had just finished solving it, its still very appreciated.

--Stephen

---

