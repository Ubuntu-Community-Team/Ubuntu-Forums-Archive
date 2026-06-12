---
title: "Bionic with two WIFI Nics."
date: 2018-08-22
forum: Networking &amp; Wireless
---

### Post by kmand on 2018-08-22
I'm running Bionic on a laptop with two Wifi adapters, a built in one that only does N, and a USB one that does "AC".
Bionic sees both and the menu elicited from the right corner panel, shows entries for both. Those entries each have there own submenu, including an "off" entry. But of I turn one "off" they both go off. In general I want to run with just the USB adapter when I'm home at my desk, but on the "N when I'm portable.

The best I can come up with is "ifconfig" off on the "N" from a terminal. However, its seems to turn itself on again after a while, presumably by the networkmanager.

Ideas? Do you agree the menu off in each menu entry turning both off is a bug?

---

### Post by TheFu on 2018-08-22
Maybe **rfkill** will let you be specific?
Also, if you disable the built-in one, then plug in the USB one, I think that will work.  We did that a few months ago at my LUG for someone in a similar situation.

BTW, many places will block wifi-N devices on their faster networks these days, making it impossible for those and G/A/B devices to connect at all.  Just beware that is possible.

---

### Post by praseodym on 2018-08-22
What about an udev-rule comparable to this one (2nd grey box, German thread)

[https://forum.ubuntuusers.de/topic/wlan-usb-8194/#post-3133322](https://forum.ubuntuusers.de/topic/wlan-usb-8194/#post-3133322)

Replace ipw2200 in that script with the module name for your internal device

---

