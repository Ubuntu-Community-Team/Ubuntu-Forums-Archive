---
title: "Boot failing at Configuring Network Connections"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by davids45 on 2006-12-11
I am running Ubuntu Dapper on an old desktop. I had set up a wireless network connection using a Netgear WG311v3 card, ndiswrapper and wpa-supplicant.  I had set this to automatically start up with Ubuntu.  

However I find that the start up hangs and fails at the "Configuring Network Connections" about 50% of the time. Occasional error displays mention ndiswrapper (but not all).

Is there some way to improve matters, or is it advisable to remove the wireless connection from start up?

Thanks for any help.

---

### Post by davids45 on 2006-12-12
Just to let anyone else know who's having network slowing-down/hanging boot issues, I found by taking out my  unconnected/still-to-be-configured Ethernet 201EA card from its slot, leaving only the working wireless card (Netgear WG311v3) in the computer, I now boot quickly, getting past the "Configuring networks" without hanging.
The old "remove the hardware, piece by piece, and see what happens" trick. The 201EA ethernet card had had its green led on so was active but driverless.

---

