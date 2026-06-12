---
title: "After Intrepid upgrade, TCP responses lost"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by jyrinx on 2008-11-06
I just did an upgrade, and now anyone on the network can't access any Web sites. The server can see them just fine, and anyone can /ping,/  but not browse.

I looked at the usual suspects - logs, Shorewall con!, etc. Got no idea what's up; any suggestions as to where to start?

---

### Post by superprash2003 on 2008-11-06
so can you ping an external website?? if so try accessing the website in your browser via ip.. type ping google.com and note down the ip and type it in mozilla firefox and see if it opens..

---

### Post by jyrinx on 2008-11-06
DNS isn't the problem. In fact, if I run curl -v google.com on the internal machine, it successfully connects and sends out the request, then hangs waiting for the response.

---

### Post by john_navarro on 2008-11-06
Is your connection over a VPN?  If so try:  sudo ifconfig ppp0 mtu 1416

You may have to change ppp0 to a different interface

---

### Post by jyrinx on 2008-11-06
Nope, no VPN.

---

### Post by jyrinx on 2008-11-06
I should note that very *small* responses get through. So if the response is an HTTP redirect, it comes through, though the page it redirects to may not. This implies that the problem has something to do with TCP fragmentation, not unlike LP #264019, though it's not the same problem: I just tried rebooting into the 2.6.24 kernel (from Hardy) and the problem didn't go away.

---

### Post by jyrinx on 2008-11-06
> **john_navarro said:**
> Is your connection over a VPN?  If so try:  sudo ifconfig ppp0 mtu 1416

Aha! You were on the right track - I set the MTU on my Internet-facing interface up to 1500 (it was at 572 or something - set by DHCP I assume?), and now stuff works again.

What should be the permanent solution here? Seems a bit odd that this would only be a problem after upgrading to Intrepid, especially given that the *user space* was the problem, not the kernel ...

---

