---
title: "Getting a working wifi Logilink 802.11ac Nano USB Adapter WL0237 (Realtek RTL8821AU)"
date: 2019-10-03
forum: Networking &amp; Wireless
---

### Post by Jaleks on 2019-10-03
After the above mentioned adapter worked fine on older Kernel version (see [this thread]("https://ubuntuforums.org/showthread.php?t=2327495")), but the [delivered source]("http://www.2direct.de/media/driver/WL0237.zip") by LogiLink does not compile any more for newer kernels (here: 4.19.0-6-amd64 / 4.19.67-2+deb10u1) there still is a solution. 
There is a compiling (and working) driver version at GitHub: [https://github.com/diederikdehaas/rtl8812AU/tree/driver-4.3.22-beta](https://github.com/diederikdehaas/rtl8812AU/tree/driver-4.3.22-beta) 
(Note that the 4.3.20 version and the 5.x versions do not include the files necessary for 8821au, so checkout the branch 'driver-4.3.22-beta' with git before compiling).

[This thread just as additional note, as my old one is not editable anymore.]

---

