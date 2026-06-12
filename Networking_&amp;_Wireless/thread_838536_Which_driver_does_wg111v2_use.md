---
title: "Which driver does wg111v2 use?"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by pytheas22 on 2008-06-23
I have a WG111v2 USB wireless card.  It sort of works out of the box in Hardy, but the connection drops about every half hour.  So I want to give ndiswrapper a shot, but I first need to know which native driver the card is using so that I can blacklist it.

Unfortunately, I can't figure out which module is driving the card.  I looked online but only see rtl* modules mentioned, and none of them are currently modprobed.  lshw for some reason doesn't tell me which module is claiming the device.  Is there anywhere else I could look to figure out what the card is using?  Or is there a way to force ndiswrapper to claim the card instead of the native driver?

Thanks in advance for any suggestions.

---

### Post by pytheas22 on 2008-06-24
For the benefit of anyone else with the same problem: through trial and error, I figured out which module is driving the card.  It's p54usb (there's also p54common and p54pci).

Also ndiswrapper doesn't seem to work, but I think it may be because my system is 64-bit.  Anyway this isn't that big of a deal to me as I have plenty of other wireless cards that work fine; I just wanted to see how Linux support for my WG111v2 was at this point, since I hadn't used it in a couple of years and was considering lending it out to a new Ubuntu user if I could get it to work reliably.

---

### Post by aimwin on 2008-07-07
> **pytheas22 said:**
> For the benefit of anyone else with the same problem: through trial and error, I figured out which module is driving the card.  It's p54usb (there's also p54common and p54pci).

Also ndiswrapper doesn't seem to work, but I think it may be because my system is 64-bit.  Anyway this isn't that big of a deal to me as I have plenty of other wireless cards that work fine; I just wanted to see how Linux support for my WG111v2 was at this point, since I hadn't used it in a couple of years and was considering lending it out to a new Ubuntu user if I could get it to work reliably.

I have wg111v2, 2 of them, I try to get work with Ubuntu 8.04, please help.
I am new to ubuntu and I am not a technical guy but try to contribute back to LINUX, especially Ubuntu.

I bought new internal wifi card belong to intel, work perfectly since the first boot, autodeted by Hardy, but I will try to work on wg111v2 until problems solved, for others out there who has wg111v2.

[http://ubuntuforums.org/showthread.php?t=850120&highlight=wg111v2](http://ubuntuforums.org/showthread.php?t=850120&highlight=wg111v2)

thanks in advance.

---

