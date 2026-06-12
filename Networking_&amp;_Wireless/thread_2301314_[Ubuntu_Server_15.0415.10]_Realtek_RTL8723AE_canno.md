---
title: "[Ubuntu Server 15.04/15.10] Realtek RTL8723AE cannot connect to WPA2/AES"
date: 2015-11-01
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2015-11-01
All details are available in [**this thread on launchpad**]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1510648").
Four options:
[LIST]
[*]wait (forever?) for an answer from the developers
[*]use **wicd** as a workaround that I already proposed [**here**]("http://ubuntuforums.org/showthread.php?t=2275970"). However:
[LIST]
[*]this package does not seem to be maintained anymore
[*]it has multiple limitations, such as regular connections drops from Android Nexus hotspot and IPv6 not supported
[/LIST]

[*]implement latest driver from **[Linux kernel available on Github]("https://github.com/torvalds/linux"). **But a few questions remain unanswered on my part:**&#8203;**
[LIST]
[*]how to compile only the realtek rtl8723ae driver and not the whole kernel?
[*]how to implement that driver into Ubuntu Server 15.10?
[/LIST]

[*]understand why the driver works on Ubuntu **Desktop** 15.04/15.10, and not on Ubuntu **Server** 15.04/15.10: does anyone has a clue?
[/LIST]

Any proposal would probably help many other people as well.

---

### Post by actionmystique on 2015-11-02
I've made some progress [**here**]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1510648/comments/6").

---

### Post by actionmystique on 2015-11-02
I've found a nice workaround **[here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1510648/comments/7") **by compiling the realtek drivers.
I'd be very glad to know why it is needed on Ubuntu Server 15.10 and not on Ubuntu Desktop 15.10.

---

