---
title: "[SOLVED] Network Manager Dropping Connection (Wireless) Reconnection Problems"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by tommohawk on 2007-12-29
Hi, I have tried looking at everyone elses problems here but still can't find the answer to my problem.

Using Ubuntu Gutsy, Intel Pro Wireless 3945 network card on an HP laptop, Linksys router.

Whenever  try to connect to my router, Network Manager keeps asking for the network key.  Sometimes it connects (eventually) after inputting the key several times and sometimes it just refuses to connect.

The encryption standard is WPA2, the ESSID is hidden and broadcast is off.  I prefer it that way for security reasons.  There are 5 other wireless networks nearby and I have made sure that my router is set on a channel which does not conflict with anyone else.

My network interfaces file is simple:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp
```

Gutsy is fully up to date and my actual wireless adapter is configured as eth1

I am using the restricted drivers included with ubuntu for the wireless.

Anyone got any ideas why this may be happening?

---

### Post by tommohawk on 2007-12-30
Thought that I would add that my other wifi devices have no problem connecting to the router and maintaining the connection.  

If I run the network restart command in  a terminal it fails eventually saying no valid DHCP offers received.

Would appreciate any help on this.

---

### Post by tommohawk on 2008-01-01
Solved this one.  It would seem that Gutsy and Network Manager do not like connections where the SSID broadcast is switched off.  Since I switched the broadcast back on it has connected without problem.

---

### Post by Sproid on 2008-01-03
Hi, I finally found a thread with a very similar problem I have, but found its solved, although mines not. I have a HP Compaq 6710b with intel/pro wireless 3945, the router is a belkin wireless g.
My problem is that after a while it drop any encrypted wireless asking for the password again and again. I solve it setting my router with no WEP or WPA/2. Other problem is that When starting ubuntu 7.10 x64 it auto connect to my neighbor wireless instead of mine that is nearest, both with no security. I don't know how to set it up it auto connect to my router. Should I open a new thread if this is marked as solve?

---

