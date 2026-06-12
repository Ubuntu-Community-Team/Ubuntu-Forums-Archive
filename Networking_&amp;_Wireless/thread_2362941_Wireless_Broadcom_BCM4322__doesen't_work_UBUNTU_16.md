---
title: "Wireless Broadcom BCM4322  doesen't work UBUNTU 16.04 TLS"
date: 2017-06-04
forum: Networking &amp; Wireless
---

### Post by babalu4u on 2017-06-04
Hi
I am new here... I install Ubuntu 16.04 TLS on my laptop compaq 6735s and wifi is not working! Can pleas somebody help... THX ;-)

[B]pci.id
[/B]
Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

**Pastebin link**

[http://paste.ubuntu.com/24769909/](http://paste.ubuntu.com/24769909/)

---

### Post by kurt18947 on 2017-06-04
I do not have this adapter so no experience. Take this for what it's worth - this might be a place to start:

[https://wikidevi.com/wiki/Broadcom_BCM94322USA](https://wikidevi.com/wiki/Broadcom_BCM94322USA)

**Probable Linux driver**
[**[COLOR=green]b43[/COLOR]**]("http://wireless.kernel.org/en/users/Drivers/b43") ([**[COLOR=magenta]in backports[/COLOR]**]("https://backports.wiki.kernel.org/index.php/Main_Page")) or [**[COLOR=brown]wl[/COLOR]**]("http://www.broadcom.com/support/802.11/linux_sta.php")
**[PCI ID first seen in kernel v2.6.30 (2009-06-10)]("https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux")**

There are wifi wizards here, I am not one.

---

### Post by jeremy31 on 2017-06-04
We can try installing firmware for the b43 module and see how it works
```
sudo apt-get update && sudo apt-get install firmware-b43-installer
```

Reboot, but I think there is a chance that it won't work, if that is the case
```
sudo apt-get install bcmwl-kernel-source
```

For this you will need to have Secure Boot disable in BIOS if this is an EFI install, then reboot

---

### Post by babalu4u on 2017-06-04
Thank you... I install firmware for b43 and now its working... :lolflag:

---

### Post by kurt18947 on 2017-06-04
:-D :grin:

---

