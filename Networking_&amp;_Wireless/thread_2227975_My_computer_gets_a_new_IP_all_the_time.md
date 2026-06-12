---
title: "My computer gets a new IP all the time?"
date: 2014-06-05
forum: Networking &amp; Wireless
---

### Post by Hund on 2014-06-05
I have 2 computers on my network. My battlestation work just fine, but my HTPC gets a new internal IP several times a day. I had this problem before, so I changed to a static internal IP and it worked just fine. But since I upgraded to the latest stable release of Xubuntu I got my dynamic IP back. And it worked just fine a few months, but now the problem is back again. And now I want to solve the problem once and for all.

Any clues?

---

### Post by TheFu on 2014-06-05
Change the DHCP lease time on the router - make it longer. I use 7 days - usually the longest allowed for portable devices.  For non-portable devices, I setup static IP leases in the router and/or static IPs on each system.

If the router will support static DHCP leases, use those.  [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

---

