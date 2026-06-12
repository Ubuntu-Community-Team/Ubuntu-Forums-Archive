---
title: "Networking doesn't remember some settings"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by jelly on 2005-09-05
Hi, I've got a wireless card and ethernet card installed in my machine, and I want by default just the ethernet card to be enabled.  In System / Adminitstration / Networking I set the wireless card to disabled and the ethernet to enabled, and all is well.  However, when I reboot both cards are enabled.. and by default it tries to use the wireless card, which has no connection.

How do I get it to remember which cards are enabled / disabled?

Thanks,

- Jelly.

---

### Post by kirsche on 2005-09-07
one way would be to edit your /etc/network/interfaces file and remove the entry for the wirlesss card under the auto section

---

