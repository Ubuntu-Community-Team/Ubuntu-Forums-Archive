---
title: "Attempting Ubuntu Wireless Router, Need help with DHCPD"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by seaward on 2006-10-25
Hi,

I'm trying to set up my ubuntu box to broadcast my internet connection to my housemates (both of them running windows xp) via a Belkin F5D6050 USB wireless card running in Ad-Hoc mode. My net connection is coming into my computer through eth0, and i am sending out with wlan0.

As far as I can tell my wireless card is operating reasonably well, though it is recognised as 802.11-DS when I believe it should be 802.11b (yet it can still receive connections and messages from other computers.)

My main struggle at the moment is in setting up a DHCP server.  I have DHCPD installed and it appears to be running correctly.  However, when my housemate's computer attempts to connect, it ends up with a self-assigned IP address and thus is unreachable from my computer.  Having checked syslog, it appears that my machine is indeed receiving the DHCPDISCOVER from the windows box (confirmed by comparing the MAC addresses) and is also offering an IP address with DHCPOFFER.  However, the windows machine is simply ignoring it, claiming it is an invalid IP address and, after several attempts, is using its own private IP.

I am sure that my housemates computer is not to blame because when my box is booted into windows xp, DHCP is working fine between our two machines.

Is there any way to find out for sure that the DHCPOFFER which my wireless card is throwing out is exactly the same as the one which the DHCP daemon is telling it to broadcast?

Does anyone have any other ideas of how to resolve this problem?

Many thanks in advance!

---

### Post by seaward on 2006-10-26
Sorry to be an attention seeker but *bump*.  Does anyone have any ideas what could be causing this issue?

---

