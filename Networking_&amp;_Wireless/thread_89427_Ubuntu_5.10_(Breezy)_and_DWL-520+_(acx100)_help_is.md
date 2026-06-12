---
title: "Ubuntu 5.10 (Breezy) and DWL-520+ (acx100) help is needed"
date: 2005-11-12
forum: Networking &amp; Wireless
---

### Post by make0007 on 2005-11-12
Installation the Ubuntu 5.10 all gone well but a problem is to but wlan card **DWL-520+** working. The card use acx100 driver and Ubuntu installed that (lsmod) directly from Ubuntu CD.

I have the access point up and running but (iwconfig or iwlist) don't show any access point available. MAC is 00:00:00:00:00:00   

Is there anybody who has the same card installed and working with Ubuntu 5.10?

---

### Post by make0007 on 2005-11-14
The solution was:

I added the 2 lines to the file:    /etc/network/interfaces

map wlan0
wireless-mode managed

and DWL-520+ is up and running with Ubuntu 5.10.

Yes, yes :p

---

