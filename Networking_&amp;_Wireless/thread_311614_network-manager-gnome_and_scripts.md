---
title: "network-manager-gnome and scripts"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Striatum on 2006-12-03
Hi all!

I connect to a WPA WLAN via network-manager-gnome and my Atheros card. Everything works fine so far.
The problem is, to get 802.11g I need to run

#iwpriv ath0 mode 0
#iwpriv ath0 turbo 1

after startup, which resets my connection. Where to put this command, so it is launched automatically before startup?
I tried /etc/network/interfaces with pre-up but that didn't seem to work.

Thank you very much!
Dominik

---

