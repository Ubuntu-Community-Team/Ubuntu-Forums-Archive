---
title: "Network Manager 0.7.0 support of multiple interfaces"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by komputes on 2008-11-15
With the introduction of Network Manager 0.7.0 I can see the possibility for Network Manager to (by default) assign multiple IP addresses (one for each connected interface). Before this, I believe NetworkManager selected one connection or the other.

I have a few questions about this:

1) Since you could theoretically be on two networks at once, what happens when traffic leaves the machine? What connection is it using? 

2) Do the two network connections balance out the traffic load? Can this be configured?

3) The options on the panel applet are  "Enable Networking" and "Enable wireless" but there is no "Enable wired connection" or "Enable eth0" (No graphical way to run "ifconfig eth0 down"). Can anyone suggest a workaround.

---

