---
title: "WG511T on edgy"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by timsan775 on 2006-11-14
I think I've been caught out by the edgy "bug" with the wireless as well.

I have just bought a new WG511T, lspci sees it fine. However, it seems that the proper modules aren't being loaded (madwifi). 

I've installed the "linux-headers", which has a madwifi directory (/lib/modules/2.6.17-10-386/madwifi). I suppose the modules are in there for the Netgear WG511T (atheros chip)? 

Which ones do I need to load (or should be loaded on boot up). I'm using 128 bit wep as well. 

t.

---

### Post by dresnu on 2006-12-15
Have you installed the restricted modules package? This is what you need to make it work.

---

### Post by dannyboy79 on 2007-02-08
edgy and wg511t is not good out of the box supposedly per this link. [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)
madwifi fixed this issue around 2/6/07 for the wg511t, Gnome NetworkManager (using wpa_supplicant, using madwifi-ng, using ath_pci).

---

