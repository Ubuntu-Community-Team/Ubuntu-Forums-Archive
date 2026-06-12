---
title: "help with USB wlan"
date: 2005-06-21
forum: Networking &amp; Wireless
---

### Post by sinisterguy on 2005-06-21
Hey everybody,

I've been using ubuntu since the 4.10 preview release (i forget what it was called, but that's what's on the old CD). I'm not super super experienced but I have no problem compiling stuff or installing kernel modules etc. Anyway, here's my problem. I have a USB WF741-UIC wireless adapter from gigafast. It uses the ZyDas chipset. I tried using the binary options available to me (wlan-ng and ndiswrapper) with no luck. thought that would be easier considering i didn't have the kernel source. Well, now I want to build the zydas module that i downloaded from another computer. It needs the kernel source though. I was wondering if there was any way that i could download it without net access on the ubuntu machine. Thanks in advance,

Lukas

---

### Post by intangible on 2005-06-21
You could use another computer to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for the source or headers (you probably just need linux-headers-2.6.10-5-686) , then download the deb from there, toss it on a CD or USB drive, afterwards just **sudo dpkg -i newpackage_whatever.deb** on the disconnected machine.

---

### Post by gub1 on 2005-08-09
I have the same usb wireless adapter, and have also tried the ndiswrapper route unsuccessfully and am relatively new to this stuff and don't understand the previous post

---

### Post by hhhzzz on 2007-03-13
i am having the same problem. I have the gigafast 11 mb wireless usb dongle ([http://www.gigafast.com/products/product_detail/WF741-UIC.htm)](http://www.gigafast.com/products/product_detail/WF741-UIC.htm)). Ndiswrapper does not work. However, there is an option to download the linux drivers from their website: [http://www.gigafast.com/products/product_drivers/WF741-UIC_drivers.htm](http://www.gigafast.com/products/product_drivers/WF741-UIC_drivers.htm)

How can I install this? what commands do I run?

thanks

haonanzhang

---

