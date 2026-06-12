---
title: "help with realtek wireless card on toshiba a210-mso"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by Greg Macinnis on 2007-12-12
Hey there all im using a realtek 8187B  for some reason ubuntu cant see it i found a driver for it but i have no idea how to install it its an internal on y laptop if that would help

---

### Post by The Tronyx on 2007-12-13
> **Greg Macinnis said:**
> Hey there all im using a realtek 8187B  for some reason ubuntu cant see it i found a driver for it but i have no idea how to install it its an internal on y laptop if that would help

I have been troubleshooting about the same thing for around 7 hours.  Here's what I have come across:
lspci | grep Real shows that it is RTL8101
lsusb also shows that 8187 is for some reason a usb device
NSIDwrapper does not like to work with the drivers
[http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/) has not helped me

If you come across anything else please tell me.

---

### Post by buccaneere on 2007-12-13
> **2point0 said:**
> I have been troubleshooting about the same thing for around 7 hours.  Here's what I have come across:
lspci | grep Real shows that it is RTL8101
lsusb also shows that 8187 is for some reason a usb device
NSIDwrapper does not like to work with the drivers
[http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/) has not helped me

If you come across anything else please tell me.

As little as I know, I did see that NDISWrapper by default will target a PCI address; not a USB. BUT, there is a way to target a USB address:

*from xeth delta & roasted*

jason@jason:~$ ndiswrapper --help
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile install driver described by 'inffile'
-a devid driver use installed 'driver' for 'devid' (dangerous)
-r driver remove 'driver'
-l list installed drivers
-m write configuration for modprobe
-ma write module alias configuration for all devices
-mi write module install configuration for all devices
-v report version information

[B]where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or '[COLOR="Red"]lsusb[/COLOR]' for the card[/B]

---

