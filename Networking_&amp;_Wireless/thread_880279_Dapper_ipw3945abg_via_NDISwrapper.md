---
title: "Dapper ipw3945abg via NDISwrapper?"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by pmurnane on 2008-08-04
Hi All:

First, please don't laugh because I'm still running Dapper. :)  I need an LTS release, and Hardy is NQTY, from my experimentations.

I have an HP dv6000 series notebook with the Intel 3945abg wireless card.  I've tried many of the posted solutions to get the ipw3945 driver to work, and none seem to do it for me.

I thought I might try NDISwrapper, but I don't know how to tell the kernel not to load the ipw3945 driver.  I'd like to do this before loading NDISwrapper so that everything stays very clean.

Any help would be appreciated.

Thanks,
--Phil

---

### Post by nittybitty on 2008-08-05
kde or gnome?

---

### Post by chili555 on 2008-08-05
Open a terminal and type:```
sudo gedit /etc/modprobe.d/blacklist
```When the text editor opens, add the following on it's own line:```
blacklist ipw3945
```Proofread, save and close. Upon reboot, *ipw3945* will not be loaded, which you can verify with:```
lsmod | grep ipw
```If this command shows no result, then it's not loaded.

---

### Post by pmurnane on 2008-08-05
nittybitty:

Gnome.  Sorry, I should have specified.  I think I'll try chili555's method and see how that works.

Thanks,
--Phil

---

### Post by pmurnane on 2008-08-05
chili555:

Thanks a bunch for the blacklist tip.  I'll give this a try, and then report back on how NDISwrapper works for my instance of 3945abg-itis.

Just out of curiosity, does anyone know whether the iwlwifi/iwl3945 drivers have settled down recently?  When I tried Hardy back in April/May, they didn't work at all for me.  That would be another possible solution, in case NDISwrapper doesn't work out.

Thanks Again!
--Phil

---

### Post by chili555 on 2008-08-05
> does anyone know whether the iwlwifi/iwl3945 drivers have settled down recently?I am running Hardy and it works perfectly for me. The package *linux-backports-modules-hardy-generic* evidently has a better driver in it and got my LED working. I think a lot of wireless issues are actually Network Manager issues. If you can scan and see networks _and_ put the correct encryption key in the correct place, ASCII, HEX, PSK, TKIP, etc., then you can connect.

I don't know how I could make my 3945ABG any better if I had the technology and the money!

---

