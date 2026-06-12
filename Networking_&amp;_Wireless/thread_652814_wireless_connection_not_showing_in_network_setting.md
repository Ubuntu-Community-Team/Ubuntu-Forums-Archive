---
title: "wireless connection not showing in network settings"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by Hightide on 2007-12-29
HI
The "Network Settings" only shows "Wired" and "Modem Connection". wireless connection is not showing


the lspci command recognises my netgear usb wireless adaptor.

help would be appreciated.:(

---

### Post by marty_oc on 2007-12-29
Do you get a message saying "restricted drivers available" ?

---

### Post by Hightide on 2007-12-29
HI
no message at all.

regards

---

### Post by marty_oc on 2007-12-29
Maybe your wireless adapter is not supported in the default installation. Please post the exact output of lspci and more information about your adapter. 

If your adapter is listed in lspci output it shows that it is physically available, but it does not say anything about installed drivers.

---

### Post by alexmoon on 2007-12-29
Not sure if this helps, but: I had a similar problem when I was trying to get Gutsy up and running, after fiddling with a few different ways of getting my wireless working. In the end I reinstalled and the wireless option has reappeared.

---

### Post by Erwin Criddle on 2007-12-29
Open a terminal windows and run ```
iwconfig
```
If no wireless devices come up on the list, then I suggest you follow a ndiswrapper tutorial.

---

### Post by ugm6hr on 2007-12-29
> **Hightide said:**
> 
the lspci command recognises my netgear usb wireless adaptor.


There is a mistake here - lspci lists PCI / PCMCIA cards - not USB.  Which is it - PCI or USB card?  Post the output from:
```
lshw -C network
```

---

### Post by boboyo on 2007-12-29
same thing happened to me yesterday. i tried everything u guys said and its still not working

---

### Post by Hightide on 2007-12-31
THanks guys

I reinstalled Gutsy and all is fine

regards

---

