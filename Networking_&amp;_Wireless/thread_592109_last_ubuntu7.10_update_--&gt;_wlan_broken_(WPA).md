---
title: "last ubuntu7.10 update --&gt; wlan broken (WPA)"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by mich123 on 2007-10-26
I installed the latest ubuntu7.10 update yesterday on my 2 laptops. On both laptops the network manager keeps asking me for entering the correct WPA-key. Playing with the keyring manager (remove key / allow network mananger etc) didn't help.

Everything worked fine before.

---

### Post by Hairy_Palms on 2007-10-26
you need to make sure gnome-keyring-daemon is running, add it to session to get it to autostart.

---

