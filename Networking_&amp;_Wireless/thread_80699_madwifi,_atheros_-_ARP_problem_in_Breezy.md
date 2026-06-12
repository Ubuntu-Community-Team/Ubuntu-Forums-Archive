---
title: "madwifi, atheros - ARP problem in Breezy"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by vimico on 2005-10-22
My setup is a DWL-650, Atheros chip set, madwifi + WPA(_supplicant) on a laptop talking to an access point which is also a router for my LAN.

The setup worked fine unter Hoary, but stopped working after upgrading to Breezy.

The symptoms are: I can access the internet from the laptop via the AP, but I can't access any service on the laptop from any other computer in the LAN.

No firewall or MAC filter are is active at the moment.

It took my some time to find the reason:

The ARP entry for the laptop is missing in all ARP caches. 

I was able to confirm that this was the reason by attempting a telnet connection from the laptop to a non-existing server on one of the other machines. The connection did fail, of course, but it stored the MACaddress in the ARP cache of that computer.

For the live time of that entry (a few minutes) connections from that machine **to** the laptop are possible.

Is this a know bug?

---

### Post by ForsBrunn on 2006-03-06
Hi Vimico,

I have an DWL-G520 and exactly the same problem as you. 

Unfortenately I haven't found any solution yet but I'm working on it. 
If you have found the solution already I would be very grateful if you posted it here, otherwise I will post the solution when I find it.

Cheers

---

### Post by ForsBrunn on 2006-03-06
Duplicated post ...

---

### Post by ForsBrunn on 2006-03-08
After some searching, I found a solution. This is a already known issue, see [http://hostap.epitest.fi/bugz/show_bug.cgi?id=63](http://hostap.epitest.fi/bugz/show_bug.cgi?id=63). This is probably already fixed in newer packages but not in the one I have in Breezy ( 0.4.5 ). I downloaded the ubuntu source package for wpasupplicant and applied the fix, compiled and installed the fixed package and now it's working.

---

