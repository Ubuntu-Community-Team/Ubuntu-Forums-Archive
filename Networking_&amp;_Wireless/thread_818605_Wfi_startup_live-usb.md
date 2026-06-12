---
title: "Wfi startup live-usb?"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by gussan-6 on 2008-06-04
Hello!

I am running Ubuntu 7.10(casper/persistent) from a USB-stick on a via-mini-itx. It works fine except that I want the wifi to start before X or gdm starts. I tried to edit /etc/network/interface but it did not work, all the changes are gone when I reboot. So I tried to customize the live-image following this link:[http://www.debuntu.org/book/export/html/216](http://www.debuntu.org/book/export/html/216),
and edit /etc/network/interface but when I boot it is all gone. So I tried to build an image from scratch following this link:[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
and change /etc/network/interface. But still the same. All changes are gone when I boot. So probably there is a script that wipes everything out that is written in /etc/network/interface. Any ideas how to solve this? I'm a newbie so examples are appreciated.

Thanks,
Gus

---

