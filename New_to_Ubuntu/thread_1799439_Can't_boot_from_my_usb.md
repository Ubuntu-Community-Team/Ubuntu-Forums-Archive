---
title: "Can't boot from my usb"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by rwscid on 2011-07-07
6 months ago I successfully loaded ubuntu 10.10 onto my usb and could boot my netbook (ASUS eee 1000HE).

Now the same usb won't boot either my netbook or this generic desktop (FOXCONN bios).

I have downloaded ubuntu 11.4, got a good md5 sum, but still the usb won't boot either computer.

Used Universal USB Installer both times (January, and now).

Boot sequence is 'removable dev' first (everything else disabled) on netbook, 'USB-CDROM' on desktop ('Removable' and 'CDROM' are other choices, neither seems to help) (and everything else disabled).

Any suggestions? GREATLY appreciated ...

Rick

---

### Post by mikenev on 2011-07-07
On a few of my machines, USB drives show up as actual hard drives rather than removable devices for booting purposes. It might be something to try. Some machines will also let you push a button during startup to bring up a boot menu, the menu usually shows detected devices.

---

### Post by Rex Bouwense on 2011-07-07
The ASUS Eee PC 1000 is one of those machines.  I have one and the USB device with the burned OS on it shows up as an additional hard drive.  Just change the order of hard drives to boot and you will be good to go.

---

### Post by rwscid on 2011-07-08
Your tip(s) worked on the ASUS netbook, and have helped me progress with the desktop, although I'm still not able to boot. Phoenix BIOS on desktop needed to be set so USB drive was forced to be considered a hard disc, not a floppy. Will re-post if can't get past current problem (USB booted Memtest86, and I'm letting it run).

THANKS FOR BEING HERE!!!!!

---

