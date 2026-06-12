---
title: "Network Manager incorrectly sees unsecured network as WPA"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by holotone on 2007-12-16
For some odd reason, network-manager decided randomly last night that my unsecured 802.11g network was running WPA and now won't let me connect without entering the "correct" passphrase. All other computers in my household can connect to the WAP fine.. It's just the laptop having problems. Rebooting does not resolve the problem.

The output of "sudo iwlist scan" also indicates that encryption is on for the network, so it's most likely a system wide problem.

Also of concern is the addition of 6 new entries for "Wired Network" in my System > Administration > Network panel. Not sure if it's related, but I thought I'd include that tidbit in case it was.

Any suggestions?

Update: I found a related unresolved bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/65225](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/65225)

---

