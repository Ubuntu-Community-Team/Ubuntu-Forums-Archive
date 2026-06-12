---
title: "Clearing Old DNS information"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by jpatt on 2006-09-28
under network settings, I keep deleting two old address only to have them reappear. I have created a location but it does not load unless I go back to network settings. Are these DNS numbers cached? Can I make my saved location the default setting? Can I edit some file?

---

### Post by wieman01 on 2006-09-28
They are cached in here:
> /etc/resolv.conf
Delete them and restart the network:
> sudo /etc/init.d/networking restart
I assume you're using DHCP?

---

