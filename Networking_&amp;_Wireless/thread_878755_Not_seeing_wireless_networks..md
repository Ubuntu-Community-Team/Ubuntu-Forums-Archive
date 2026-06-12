---
title: "Not seeing wireless networks."
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by PauLrus on 2008-08-03
I'm running ubuntu with the ar5006eg chipset. My friend got that working yesterday at our friends' house but now that I've brought it home I can't even see my network. I've tried the "connect to another network" with no success and also no error message it just recycles my back to the window where I type in the passphrase.

ar5006eg chipset
linksys wrt54gs v. 7.2.03
latest ubuntu

Thanks for your time and any more information you need I would be glad to give to you. Thank you.

---

### Post by caljohnsmith on 2008-08-04
Please post the output of the following commands:
```
ifconfig
iwconfig
sudo lshw -C network  (just paste the part pertaining to your wireless NIC)
```
And also, if you run:
```
sudo iwlist scan
```
Does it show any available networks?

---

