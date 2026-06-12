---
title: "Wireless card detected but would rather do it myself"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by Mikeee on 2006-08-03
Hi all,

Ive just installed the new ubuntu-desktop version. It detected my wireless pci card automatically but when i went to configure it it didnt connect to my router. I know i can get it working with ndiswrapper but i believe i'll need to uninstall the current wireless drivers so there is no conflict between ndiswrapper and the default installed drivers. How can I do this? Thanks

---

### Post by beemer on 2006-08-03
I think you can use lspci to find what's being loaded for your wireless card.

Then add a blacklist line to /etc/modprobe.d/blacklist like:

blacklist drivername

Beemer

---

### Post by beemer on 2006-08-03
I think you can use lspci to find what's being loaded for your wireless card.

Then add a blacklist line to /etc/modprobe.d/blacklist like:

blacklist drivername

Beemer

---

### Post by gerscht on 2006-08-03
which card is it?
if it has a ACX 111 chip (just by chance, as I had the same problem => detected, but not configured...) then you just have to remove the symlink in /lib/firmware/[your kernel]/acx/default/[your chip here] (which points to version 2.3.1.31) and set it firmware 1.2.1.34. After a reboot it should work well.
Hope this helps,
gerscht

---

