---
title: "looking for lts 18.04 wifi dongle 802.11AC"
date: 2018-06-11
forum: Networking &amp; Wireless
---

### Post by hueyhoolihan on 2018-06-11
just upgraded to Ubuntu LTS 18.04 and now my wifi dongle doesn't work anymore. i suspect the driver, that i had to recompile with every kernel update (starting with 16.04), is not (no surprise) in the new LTS 18.04 and my attempts (over 12 hours of work) to compile it, like i had in the past, have failed, mainly because the new gcc compiler options won't successfully compile the rtl8812au source code that i've downloaded from git.hub (several flavors of it). BTW, i've had other problems compiling and running my custom NASM source code using Xlib subroutines too (another sad story...). 

soooo, anybody got a line on a wifi usb dongle i can plug into my intel Nuc that will work?

solved. go to... 
 [https://www.erol.name/compile-realtek-rtl8812au8821au-usb-wifi-driver-debian-jessie/](https://www.erol.name/compile-realtek-rtl8812au8821au-usb-wifi-driver-debian-jessie/)

---

### Post by him610 on 2018-06-12
Both of these work out of the box using Ubuntu

Edimax EW-7811Un 150Mbps 11n Wi-Fi USB Adapter
[https://www.amazon.com/gp/product/B003MTTJOY/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B003MTTJOY/ref=oh_aui_detailpage_o03_s00?ie=UTF8&psc=1")

TP-Link N300 Wireless Mini USB Adapter
[https://www.amazon.com/gp/product/B0088TKTY2/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B0088TKTY2/ref=oh_aui_detailpage_o05_s01?ie=UTF8&psc=1")

You might want to get Chilli555 (he hangs around the Networks forum) to give his opinion.

---

### Post by hueyhoolihan on 2018-06-14
thanks. appreciate the response. although i finally got my dongle to work, i still must recompile when the kernel is updated. PITA. so may try one of the ones you recommended.

---

### Post by jeremy31 on 2018-06-15
Moved to Network and Wireless, what source code are you using for the dongle?

---

### Post by chili555 on 2018-06-15
> You might want to get Chilli555 (he hangs around the Networks forum) to give his opinion.
Please see my post #22 here: [https://ubuntuforums.org/showthread.php?t=2359573&highlight=thinkpenguin](https://ubuntuforums.org/showthread.php?t=2359573&highlight=thinkpenguin)

---

