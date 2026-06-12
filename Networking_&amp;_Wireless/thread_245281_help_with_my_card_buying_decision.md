---
title: "help with my card buying decision"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by sal on 2006-08-27
Im going to buy a "zonet zew1502" wfi pcmcia card and am woundering if anyone has any knowledge of this card. supposedly its supposed to work OOTB in Linux but Im woundering if anyone here has experiance with this card or further knowledge of it.

here is a link to the card at newegg:
[http://www.newegg.com/Product/Product.asp?Item=N82E16839130011](http://www.newegg.com/Product/Product.asp?Item=N82E16839130011)

thanks in advance for any help,
sal

---

### Post by tturrisi on 2006-08-27
Cheap priced card but uses a Marvel chipset, thus to get it to work you will have to use ndiswrapper in linux...can be a real pain in the arse.  Best to look for a card with an atheros chipset.

---

### Post by SnackySmores on 2006-08-27
check this out [http://lists.chambana.net/mailman/archive/cu-wireless-dev/2006-June/001284.html]("http://lists.chambana.net/mailman/archive/cu-wireless-dev/2006-June/001284.html")
they have a list of some cards with the atheros chipset
take care

---

### Post by sal on 2006-08-27
thanks for all the help. this is the card im going with:

Atheros AR5002X_Wireless 802.11abg_108mps_Mini PCI

should that work "right out of the box" or am i going to have to do some hacking around?

thanks in advance for all the help,
Sal

---

### Post by tturrisi on 2006-08-27
WAIT!!!
In your first post you were looking at a pcmcia cardbus adapter and now you want a minipci adapter.

mini-pci:  [http://en.wikipedia.org/wiki/Mini_PCI](http://en.wikipedia.org/wiki/Mini_PCI)
pcmcia & cardbus:  [http://en.wikipedia.org/wiki/Cardbus](http://en.wikipedia.org/wiki/Cardbus)

---

### Post by sal on 2006-08-27
> **tturrisi said:**
> WAIT!!!
In your first post you were looking at a pcmcia cardbus adapter and now you want a minipci adapter.

mini-pci:  [http://en.wikipedia.org/wiki/Mini_PCI](http://en.wikipedia.org/wiki/Mini_PCI)
pcmcia & cardbus:  [http://en.wikipedia.org/wiki/Cardbus](http://en.wikipedia.org/wiki/Cardbus)

yes i know what the deferance is, my laptop takes both.

---

### Post by funchords on 2006-08-28
Should work right out of the box.

---

### Post by tturrisi on 2006-08-28
Atheros chipsets won't work out-of-the-box with a hard drive install.  You will need to install the linux-restricted-modules that match your kernel.  After that, the card will get detected & drivers loaded at boot and it will work.

---

### Post by sal on 2006-08-28
thanks for the info.
as long as i dont have to fuss with ndis and broadcom, im fine.

---

### Post by funchords on 2006-08-28
> **tturrisi said:**
> Atheros chipsets won't work out-of-the-box with a hard drive install.  You will need to install the linux-restricted-modules that match your kernel.  After that, the card will get detected & drivers loaded at boot and it will work.

I use the Intel ipw drivers, which are also restricted, yet wifi worked right after installation.

YMMV, but that's what happened to me.

---

