---
title: "Acer Aspire 3690 Air force one"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by AJB2K3 on 2008-09-14
Ok I have an Aspire 3690 with the broadcom AF1 chip set, it was working for a while now its stoped completly.
Its finding networks but when I try to connect the two green lights on the icon stay dark and do nothing and after a long while pops ups the pasword request.

Can anyone help me or sugest a mini pci wifi card that's actually supported by the kernal?

---

### Post by lian1238 on 2008-09-14
I had that problem before on my Acer Aspire 5590. Try switching the wireless security type to other types.

---

### Post by AJB2K3 on 2008-09-14
yep tryed that and got noware.

---

### Post by lian1238 on 2008-09-14
Might be a silly question but, is there a chance that the passkey is incorrect?

---

### Post by AJB2K3 on 2008-09-15
Ok after rembering to use **Dmesg** I found
```
[  638.592273] wlan0: Initial auth_alg=0
[  638.592279] wlan0: authenticate with AP 00:1b:9e:97:17:9c
[  638.597213] wlan0: authenticate with AP 00:1b:9e:97:17:9c
[  638.632425] wlan0: authenticate with AP 00:1b:9e:97:17:9c
[  638.656027] wlan0: authentication with AP 00:1b:9e:97:17:9c timed out
[  639.304931] b43-phy0 debug: Disabling hardware based encryption for keyidx: 0, mac: ff:ff:ff:ff:ff:ff
[  648.167363] eth0: no IPv6 routers present

```
Can anyone help?

---

