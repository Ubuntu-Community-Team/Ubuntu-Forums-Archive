---
title: "Proxim Orinoco USB Card"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by DoubleBiox on 2007-10-27
I have the proxim b11FNF-USB and by checking out the windows drivers for the card I found refrences to orinoco, which confirmed what I suspected that this is an orinoco card.

Next I ran before inserting the usb connector:

```

lsmod | grep orinoco
lsmod | grep prism2
lsmod | grep hostap

```

nothing returned and also I after I insert the usb connector.  However, in hardware info a device is registering as being plugged in.

I then downloaded the drivers and had the same problems that everyone else seems to be having and I get "Wireless Extensions are not enabled"

But then I found this link which seems to suggest that they may use a prism chipset.  Any Ideas on where to go from here?

[http://osdir.com/ml/linux.drivers.orinoco.devel/2005-10/msg00010.html](http://osdir.com/ml/linux.drivers.orinoco.devel/2005-10/msg00010.html)

[This is the card that I have.  I have the orinoco silver editon]("http://www.proxim.com/products/wifi/client/11busb/index.html")

I belive I need wavlan drivers based on what i've been able to find out abut the card.

---

### Post by DoubleBiox on 2007-10-27
no longer an issue!

---

