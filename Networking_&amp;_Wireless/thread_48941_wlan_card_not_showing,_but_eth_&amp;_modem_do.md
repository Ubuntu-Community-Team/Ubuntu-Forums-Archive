---
title: "wlan card not showing, but eth &amp; modem do??"
date: 2005-07-14
forum: Networking &amp; Wireless
---

### Post by octal_forty on 2005-07-14
I have a machine with a PCI 56k modem, PCI ethernet card and a PCI wireless netgear wg311t card.

The first 2 (modem and ethernet) both show up when I click on the Network setting window. Something like: modem0 and eth0 are listed. but no wlan0 is listed?

Do I need to do something to activate the card with ubuntu?
Or does this mean that the card is not supported by ubuntu?

---

### Post by txgeek on 2005-07-14
The wg311v1 uses the Atheros chipset which works with Madwifi.  The wg311v2 uses the ACX111 (not ACX100) chipset which requires ndiswrapper and the wg511v2.inf from the driver CD.

---

### Post by octal_forty on 2005-07-14
1. How do i tell if i have v1 or v2.

2. If i have wg311v2 do i need the wg(5)11v2.inf or the wg(3)11v2 from the driver CD.?


Sorry (complete noobie)
Cheers.

---

