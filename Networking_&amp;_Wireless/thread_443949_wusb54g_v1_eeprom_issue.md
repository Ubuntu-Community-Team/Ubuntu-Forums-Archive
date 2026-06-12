---
title: "wusb54g v1 eeprom issue"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by buMPer on 2007-05-14
hi all

my linksys wusb54g v1 usb wireless adapter is driving me crazy.  i looked everywhere and all HOWTO's that i found on this forum are for 32-bit machines.  i did "dmesg" and this is what i found:

```

[ 121:  823543] p54u: lm86 firmware
[ 124:  017306] prism54usb:  eeprom read failed!
[ 124:  017328] prism54usb:  probe of 2-9:1.0 failed with error -22
[ 124:  017428] usb core: registered new interface driver prism54usb

```

can someone tell my tiny brain what's going on and a solution is definitely highly appreciated.

here's my spec:
athlon x86-64 X2 4400
asus a8n32sli
2 gig ram
1 sata hard drive
linksys wusb54g v1 usb network adapter

TIA!!!

---

### Post by kismet-sl on 2008-03-09
Which version of Ubuntu are you using?

Have you already checked the following bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90902](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90902)

Try to update your linux-image-generic to the latest available.

Ciao,
Stefano "Kismet" Lenzi

---

