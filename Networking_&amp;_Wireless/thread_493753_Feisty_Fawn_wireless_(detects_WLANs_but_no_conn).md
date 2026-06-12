---
title: "Feisty Fawn wireless (detects WLANs but no conn)"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by gnudiff on 2007-07-06
Hello,

I just installed the newest Ubuntu (7.04) on my brand new Asus U5F (ID: 1A). Applied all the system updates.

Everything seems to work good, except the networking. I looked around the forums, but didn't find any solutions yet.

Main problem is with wireless:

- Wireless card is detected and shows up in "Restricted drivers" window as:
 Intel(R) Pro?Wirless 3945 Network Connection Driver for Linux, Enabled, In Use.

* Wireless networks ARE detected OK, BUT attempting to join any (unsecured) one just fails!
the status text on Network Manager applet, says: "Attempting to join wireless network XXXXX" and then after some time just says "network is not connected".

The syslog shows something like:
```
NetworkManager: Activation (eth1/wireless): association took too long (>120s), failing activation.
Activation (eth1) failure scheduled...
Activation (eth1) failed for access point (XXXXX)
```

This is the same for all the unsecured wireless access points I tried, signal strength is from 40%-70%.
Here is what says iwconfig (I omit some things, since I am retyping this by hand):

```
eth1 IEEE 802.11g ESSID: "My Wireless Network A"
Mode: Managed  Frequency: 2.452GHz
Bit Rate: 36 Mb/s   Tx-Power:15dBm
Retry Limit: 15  RTS thr:off   Fragment thr: off
Encryption key: off
Power Management:off
Link Quality=86/100 Signal level=-68 dBm Noise level=-69 dBm
Rx invalid nwid: ... (all these are 0 except):
Invalid misc: 5289
```

The secondary problem is with RJ45 network connection.

Essentially, UNLESS wired network is connected at boot time, Network Manager applet keeps greyed out "Wired Network" option even after I connect the cable... major frustration.

If I try to do "Network settings" manually, "Wired Connection" shows with checkbox at it and dhcp(correctly).

Major showstopper, since there seems to be no way to get network connected unless you stick in cable at boot time. 

Any hints/suggestions very much appreciated.

---

