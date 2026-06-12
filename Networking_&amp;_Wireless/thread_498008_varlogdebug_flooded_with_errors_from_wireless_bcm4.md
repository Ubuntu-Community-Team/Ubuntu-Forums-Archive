---
title: "/var/log/debug flooded with errors from wireless bcm43xx"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by KyleBrandt on 2007-07-10
My /var/log/debug and dmesg are always being flooded with the following error:
```
Jul 10 21:19:48 [My Hostname] kernel: [10296.668000] TKIP: received packet without ExtIV flag from 00:13:46:[##:##:##]
```

I also get:

```
J...kernel: [10605.768000] TKIP: replay detected: STA=00:14:bf:...... previous TSC 00000000063a received TSC 00000000006d
```

I have a Broadcom wireless card using the bcm43xx driver, and am using WPA.  I have installed the wpa supplicant and fw-cutter.  The wireless connection works fine.

Anyone have any ideas?

---

### Post by Mr. C. on 2007-07-11
These may be inocuous, or may indicate a hack attempt.

The first one is from some DLink hardware.  The second one is from some Cisco/Linksys hardware.

Do you have devices from those vendors, with those MAC addresses ?

MrC

---

### Post by KyleBrandt on 2007-07-11
None of my hardware has those addresses (Including all of the routers macs as well as clients).  I have had those notices since I installed the wireless driver I think.  Possibly the MACs in the error messages have changed.  Maybe they are some sort of collisions from other wireless networks?

---

### Post by Mr. C. on 2007-07-11
Those MAC addresses then are likely those of one or more neighbors.  The first three parts indicate the vendor.  They won't be changed unless someone intentionally changes them.

The replay detected message indicates a packet came back with the same data, but a different checksum.  This is what can happen if someone is capturing your traffic, and playing it back with their changes (called a replay attack).  I'd do a little more investigation.

I'm not sure about the other one, but it may be related to:

[http://hostap.epitest.fi/bugz/show_bug.cgi?id=126](http://hostap.epitest.fi/bugz/show_bug.cgi?id=126)

Is your kernel version prior to 2.6.17 ?

MrC

---

### Post by KyleBrandt on 2007-07-11
2.6.20-16-generic #2 is my current kernel.  I seem to get these errors when I go to different locations, so I don't think I am going to worry about it to much.  But I will read up on replay attacks.

---

