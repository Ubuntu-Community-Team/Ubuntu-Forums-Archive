---
title: "Usb 3.0"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by daniell59 on 2010-11-25
I was wondering whether Ubuntu will detect a USB 3.0 PCI-Express Card. I was considering the purchase of  [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6509554&SRCCODE=LINKSHARE&cm_mmc_o=-ddCjC1bELltzywCjC-d2CjCdwwp&AffiliateID=Es5Ekr9eEBk-o8tzKD7whQ76x9MJlwLNVg](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6509554&SRCCODE=LINKSHARE&cm_mmc_o=-ddCjC1bELltzywCjC-d2CjCdwwp&AffiliateID=Es5Ekr9eEBk-o8tzKD7whQ76x9MJlwLNVg)

---

### Post by halj32 on 2010-11-25
I heard that Linux was the first kernel to include usb 3, that was earlier this year so if you have a new kernel it should work

---

### Post by agarzon on 2010-12-10
I am currently having problems with a different USB 3.0 PCIe card. Ubuntu does not run it, even though it sees it when listed with lspci

---

### Post by khelben1979 on 2010-12-11
USB 3.0 support was implemented in Linux kernel 2.6.31 according to [this source]("http://www.linux.com/news/hardware/peripherals/278579-linux-and-usb-30").

This means that Ubuntu 10.04 and upwards have USB 3.0 support but not previous versions of Ubuntu. In my opinion, I believe that a bit more expensive variant of the card would work better, such as if you choose a card from Belkin, but I cannot confirm it.

---

### Post by haphaeu on 2010-12-11
> **agarzon said:**
> I am currently having problems with a different USB 3.0 PCIe card. Ubuntu does not run it, even though it sees it when listed with lspci

same for me, got a US Robotics, [USR8402]("http://www.usr.com/support/product-template.asp?prod=8402"), with a popular NEC controller, and I've just spent my whole Saturday trying to get it to work.

it is listed in lspci:

```
$ lspci | grep NEC
04:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)

```

even in WinXP this new toy is giving me problems. it works fine, more than 3x faster than USB 2.0, but after some time, windows gives a "delayer write failure". but that's another thing.

i would like to get this board working under linux. but no clues at all so far...

Cheers,
Haphaeu

---

### Post by haphaeu on 2010-12-13
just a brief update: I was trying in Fedora 11, but it doesn`t support USB 3.0. So I've updated to Fedora 13 and my pretty little board is working now :)
not fully tested yet. I'm working on this and let you know...

edit: card recognized. but very unstable. every time large files are transfered, an error occurs. considering the error under linux and winxp, I guess my card is not that good... :(   NOT recommended!!

---

### Post by cascade9 on 2010-12-13
I've been running a USB3.0 controller for a few months now, no issues. Mind you, its not an addon card (its on the motherboard) and not with ubuntu, I'm using aptosid on that boxxen.... 

```
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
```

---

### Post by scheuri on 2010-12-13
Hi all

please be aware that USB-3.0 "awareness" and drivers for different boards are not the same thing.

While linux technically knows USB-3.0 for some time already (at least in a generic fashion), not all different boards, chips and whatnot are supported.

So, you might be lucky enough that drivers for your specific device are in the kernel or the generic one might work for you. Otherwise you need to wait for someone to program a driver for you.

For Windows, I am pretty sure, the drivers will be delivered either with a CD or via download to install and get ready. Something that needs a bit more work within linux I am afraid.

cheers
scheuri

---

