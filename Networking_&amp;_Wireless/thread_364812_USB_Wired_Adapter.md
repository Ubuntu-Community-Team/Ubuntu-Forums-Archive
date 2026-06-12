---
title: "USB Wired Adapter"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Chaos5lw on 2007-02-18
Hi, quick question. I'm considering using this with a laptop to get a wired LAN connection under Ubuntu 6.10 Server and was wondering if it would work.

Its a USB to RJ-45 connector.
[http://www.dabs.com/productview.aspx?Quicklinx=3V6D&CategorySelectedId=11175&PageMode=1&NavigationKey=11175,4294960491,47510000,4294960483](http://www.dabs.com/productview.aspx?Quicklinx=3V6D&CategorySelectedId=11175&PageMode=1&NavigationKey=11175,4294960491,47510000,4294960483)

---

### Post by gradedcheese on 2007-02-18
'might work.  The ones I've used are supported by the "asix" driver (because they have the corresponding chipset).  If that one is the same, then it will work fine.  You might need to build/install a newer asix driver, but that's about it (it's not very hard to do).  There are very few usb-net drivers though:

```

ls /lib/modules/2.6.17-10-386/kernel/drivers/usb/net/
asix.ko  cdc_ether.ko   gl620a.ko   pegasus.ko     rt2570      zaurus.ko
atmel    cdc_subset.ko  kaweth.ko   plusb.ko       rtl8150.ko  zd1201.ko
catc.ko  eagle          net1080.ko  rndis_host.ko  usbnet.ko

```

so if you have one of these chipsets, it probably works ;)  Try and see if google (for that device's name + "linux" or something) turns up the chipset name.

---

### Post by Chaos5lw on 2007-02-19
Ok, thanks.

How well is this likely to work?
[http://www.dabs.com/productview.aspx?Quicklinx=3ZQK&CategorySelectedId=11175&NavigationKey=11175,4294955386,4294960491](http://www.dabs.com/productview.aspx?Quicklinx=3ZQK&CategorySelectedId=11175&NavigationKey=11175,4294955386,4294960491)

---

### Post by gradedcheese on 2007-02-19
according to Google, that one works.

---

