---
title: "Router does not DHCP to a different OS"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by leohart on 2007-08-25
My router is a brand new Dlink with WPA-PSK TKIP and DHCP enabled.

When I first connect to this router using Ubuntu, I get a DHCPOFFER just fine. Booting into Windows and the wireless connection nevers get a DHCPOFFER.

Reset router. 

Try again this time with Windows first and it gets a DHCPOFFER right away. Try with Ubuntu and it doesn't work. 

Is this a known problem with WPA-PSK or TKIP ? Or is it something else that I am missing.

Of course, this is on the same computer and the same NIC.

---

### Post by leohart on 2007-08-25
I found the problem myself. It was because I had the wireless router configured to work in WPA2 mode. 

Switching back to WPA works.

---

