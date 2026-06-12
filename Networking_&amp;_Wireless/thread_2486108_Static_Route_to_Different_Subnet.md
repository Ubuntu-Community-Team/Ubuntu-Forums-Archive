---
title: "Static Route to Different Subnet"
date: 2023-04-20
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2023-04-20
Folks,  just practising something to understand security issues I created a static route within my TP-Link router to a different subnet address to that which is set in the router.

Now it all works, my main IP range (A) works as intended and my Raspberry Pi connected to subnet (B) can access the internet fine.

What puzzles me though is my main subnet (A) can ping and access the second subnet (B) and subnet (B) can ping and access anything (if it is permitted) in subnet (A).

I was under the impression creating a static route in my router would allow the second subnet internet access but not LAN access.

Appreciate my TP-Link Model No. TD-W9970 is not the most elaborate of devices but thought the second subnet would be isolated.

Geoff

---

### Post by aljames2 on 2023-04-24
On your LAN, you would look for setting(s) in your router that denies incoming traffic to your LAN interface.  Most routers default to deny incoming & allow outgoing traffic on all interfaces.  Double check your traffic settings.  You may have opened up your LAN net more than intended.

Side note, it is always good to check that your device firmware is running on the latest version.

---

### Post by Geoff_Lane on 2023-04-25
> **aljames2 said:**
> On your LAN, you would look for setting(s) in your router that denies incoming traffic to your LAN interface.  Most routers default to deny incoming & allow outgoing traffic on all interfaces.  Double check your traffic settings.  You may have opened up your LAN net more than intended.

Side note, it is always good to check that your device firmware is running on the latest version.

The firewall appears to have no effect on local traffic, merely on traffic going out to WAN or incoming.  The router defaults to denying any non established connections so I seldom used the firewall.

Geoff

---

