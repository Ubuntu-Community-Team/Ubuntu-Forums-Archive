---
title: "firestarter cutting off thin clients"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2008-01-29
I had three thin clients happily booting off an Edubuntu server until I installed Firestarter. The installation went smoothly enough (I configured Firestarter to share my internet connection and use dhcp for the LAN), but my clients were immediately cut off and couldn't boot back in.
I completely uninstalled Firestarter but the clients are still getting hung early in the boot process (waiting for an ip address that never arrives). I suspect that the system is still using the dhcpd.conf file in dhcp3 rather than the dhcpd.conf in ltsp. If that's the case, how would I reset that and what other conf files might need changes?
Also: does anyone have any idea why I can't boot clients with Firestarter?
Thanks,
David

---

### Post by dbclinton on 2008-01-29
bump

---

### Post by dbclinton on 2008-02-22
I still don't understand what firestarter was up to, but (with a smart suggestion from a friend) I did solve the thin client booting problem: it was a simple matter of resetting my Gigafast five port network switch (by pulling its plug and letting it restart). Don't know why, but that did it.

---

