---
title: "Installing wirless usb drivers on xbuntu"
date: 2013-09-11
forum: Networking &amp; Wireless
---

### Post by eth0up on 2013-09-11
hello im running xubuntu 3.8 fully updated :P
im trying to set up this card [http://www.ebay.ca/itm/TELUS-Sierra-Wireless-USB-306-Internet-Stick-Free-Shipping-/300963134066?pt=US_Mobile_Broadband_Devices&hash=item4612ccfa72](http://www.ebay.ca/itm/TELUS-Sierra-Wireless-USB-306-Internet-Stick-Free-Shipping-/300963134066?pt=US_Mobile_Broadband_Devices&hash=item4612ccfa72)
and im having troubles could anyone tell me what chipset it has XD
also can this card work as a normal day to day internet card ?

---

### Post by varunendra on 2013-09-11
Please open a terminal (Ctrl+Alt+T) and post the outputs of  -
```
lspci -nnk | grep -iA2 net
```

This will give a precise information of the card and the driver in use, if any.

---

