---
title: "Toshiba Notebook w/Atheros AR5006EG not working"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by stryder76 on 2006-09-04
Hello everyone.  I'm new to Linux (but have used Mac OS X since 1997, and Windows since 1993 {poor me}), and I can't get the wireless working on my Toshiba Satellite A110 notebook.

The notebook uses the Atheros AR5006EG chipset, which I think is brand new (as of July/06).

Ubuntu doesn't even see it.  Any suggestions?

Thanks!

Stryder (Canadian, eh!)

---

### Post by garrye on 2006-09-05
Just cuz yer a Canadian (EH!) I gotta bust out a reply!!!  Canuck to canuck I'm using a card that sports AR5212 Atheros silicon and the builtin madwifi driver picks it right up.  This card appears in winbloze as an ar5001x.  Maybe because yours is a newer one it won't pick up.  But look into the madwifi thing.  That's what should pick it up and make it work.  If you're using Network Manager try ditching it and run with wpa_supplicant if you're trying to do the WAP thing.  Also try an unsecured/WEP network if you can get your hands on one.  That will save you from having to mess with the wpa layers.  Also try coding "lspci | grep Atheros" in a terminal window.  Make sure you type CAPITAL A theros. Here's what mine gives:

dad@dad-buntu:~$ lspci | grep Atheros
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

That will tell you if the driver is loading.

Good luck - tinker on!!!

---

