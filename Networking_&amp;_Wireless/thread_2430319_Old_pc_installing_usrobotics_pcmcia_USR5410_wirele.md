---
title: "Old pc: installing usrobotics pcmcia USR5410 wireless card driver"
date: 2019-10-30
forum: Networking &amp; Wireless
---

### Post by kovenant-i on 2019-10-30
Hi,
This old notebook, a Toshiba Satellite L30-10T, has a built in wireless card that makes many versions of linux crash.
To solve this, I've bought an used  usrobotics pcmcia USR5410 wireless card.

According to the manufacturer website, there were once official linux drivers (that's why I bought it in the first place) [https://support.usr.com/support/product-template.asp?prod=5410](https://support.usr.com/support/product-template.asp?prod=5410)
I can't find those drivers anymore, so I tried googling and I found this guide [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php) that explains how to build them from source.

I'm trying following the guide, but during compiling I get stuck to
```
 sudo make
Kernel version file: /lib/modules/5.0.0-32-generic/build/include/linux/version.h
Kernel configuration file: /lib/modules/5.0.0-32-generic/build/.config
Make damn sure these really match your currently running kernel!!

grep: /lib/modules/5.0.0-32-generic/build/include/linux/version.h: File o directory non esistente
Kernel configuration found, performing sanity checks
All of the following items are required by the driver:
    Loadable modules support is enabled.
    Wireless LAN (non-hamradio) support is DISABLED!
    Wireless extensions support is DISABLED!
The following is needed for PCMCIA/CardBus cards:
    PCMCIA support is enabled.
    CardBus support is enabled.
The following is needed for USB card support:
    USB support is enabled.
The following is needed for PCI card support:
    PCI support is enabled.
Kernel configuration lacks needed options, please correct! ABORTING.
Makefile:12: recipe for target 'config.mk' failed
make: *** [config.mk] Error 1


```

Any help?

---

### Post by chili555 on 2019-10-30
Did you notice this at the top of the linked page?

[SIZE=3][COLOR="#FF0000"]NOTICE: This guide DOES NOT APPLY to kernel version 2.6.14 or later.[/COLOR][/SIZE]It means what it says. This moldy old thing will never compile on a 5.0 kernel. Ever.

As far as Google and I can find, the acx100 driver project is long since dead.

Did you consider a USB wireless device?

There are but a precious few of us here on the forum that even know what PCMCIA is!

---

### Post by kovenant-i on 2019-10-31
The problem is that this old piece of crap of a NB has got a single usb, and the owner wants it for something else. I bought this card thinking it would work out of the box with linux, but I was wrong. I probably need to buy another one that does.
At least as long as someone else has another solution.

---

### Post by chili555 on 2019-10-31
> At least as long as someone else has another solution.Please check here: [https://www.amazon.com/NETGEAR-RangeMax-Wireless-N-Notebook-Adapter/dp/B000FFLYI2/ref=sr_1_3?keywords=pcmcia+wireless&qid=1572535585&sr=8-3](https://www.amazon.com/NETGEAR-RangeMax-Wireless-N-Notebook-Adapter/dp/B000FFLYI2/ref=sr_1_3?keywords=pcmcia+wireless&qid=1572535585&sr=8-3)

Check the answered questions for 'linux.'

Please note that, due to the ancient PCMCIA technology and the age of these dinosaurs, the card will likely only do WEP and not WPA2. WEP is rather insecure.

Also, none will likely do anything faster than 802.11G.

---

### Post by kovenant-i on 2019-10-31
I can't use wep. Normally I search ebay and find a lot of cards. I just need to know which card I can buy that will work for sure with the current linux kernel.

---

### Post by praseodym on 2019-11-01
What about an USB hub? Is that suitable?

---

