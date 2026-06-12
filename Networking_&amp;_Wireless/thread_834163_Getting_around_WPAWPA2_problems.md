---
title: "Getting around WPA/WPA2 problems?"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by hajk on 2008-06-19
I've posted in the Apple section of the Ubuntu forum about my problems getting the Broadcom 4328 rev 05 wireless chip on my MacBook Pro to work using ndiswrapper. To make a long story short, a wireless connection with WPA/WPA2 Personal security cannot be made, with network-manager (or wicd or wpa_supplicant) asking repeatedly and unendingly for the WPA passphrase and the encryption used. Not sure what the problem is, it seems that something is timing out, or whatever.

A connection is easily established without such security, however. Could somebody enlighten me on the pros and cons (the cons, actually) of configuring the AP to limit wireless access to the known list of MAC adresses of my computers? Is this safe?

---

### Post by pokipoki08 on 2008-06-19
I'm also having the same problems, using iMac LCD and Broadcom 4328. Have tried with windows drivers (copied from System32 dir), bootcamp beta and Leopard drivers.

No go.

You may want to try booting and testing with the Hardy CDROM, like what I did here.

[http://ubuntuforums.org/showthread.php?t=833868](http://ubuntuforums.org/showthread.php?t=833868)

Maurice

---

### Post by hajk on 2008-06-19
Thanks, I had already tried that but it doesn't work (yet) with the rev 05 version of the Broadcom 4328. I understand that it does work with the rev 03 version, though.

So, that's why I want to know whether having only MAC address restrictions is safe -- I guess neighbours can't have a free ride in that case, but can they easily intercept  and understand any of my wireless traffic? What could the consequences be?

---

