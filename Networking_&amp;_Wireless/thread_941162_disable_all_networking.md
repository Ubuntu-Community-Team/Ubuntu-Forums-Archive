---
title: "disable all networking"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by wildman4god on 2008-10-07
This will sound strange to alot of people, but I want to know how to disable basic networking on bootup (please don't ask why), In the end I want to make it as hard as possible to reinable internet access, I have already uninstalled every browser and programs with browsers, I have removed network manager, tools etc. I was going to remove netbase package but it wouldn't do it without removing alot of nessissary programs. also on a side note, in ifconfig, it is showing 2 vmnet interfaces, how do I get rid of them, it annoys me. also keep in mind i still want usb devices, like flash drives and webcams, etc to still work, and parrallel abd rs-232 db9 serial.

---

### Post by Iowan on 2008-10-07
Remove **/etc/init.d/networking**. Might also scour /etc/rcX.d directories for network-related "S" files. **ifconfig** could be renamed (or removed).

---

### Post by bowens44 on 2008-10-07
Yank your wireless card or unplug your cable.

---

### Post by espressobeanie on 2010-02-06
That doesn't disable a kid from sticking a usb wifi dongle into his usb ports. Stick hot glue in the ethernet jack. And if you truly want to disable the ethernet, boot in your bios and see if there's a setting to switch it off.

---

