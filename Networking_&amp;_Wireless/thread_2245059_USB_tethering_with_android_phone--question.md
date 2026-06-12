---
title: "USB tethering with android phone--question"
date: 2014-09-20
forum: Networking &amp; Wireless
---

### Post by remn on 2014-09-20
I'm trying to set up USB tethering between my galaxy s2 and my ubuntu laptop. I'm using the following how-to:

[https://wiki.archlinux.org/index.php/Android_tethering](https://wiki.archlinux.org/index.php/Android_tethering)

At one point it says to run ip link in a terminal, and then: "[COLOR=#000000][FONT=sans-serif]You should be able to see a [/FONT][/COLOR]usb0[COLOR=#000000][FONT=sans-serif] or [/FONT][/COLOR]enp?s??u?[COLOR=#000000][FONT=sans-serif] device listed like this (notice the enp0s20u3 device).[/FONT][/COLOR]" But neither of these devices show up in the output when I run ip link. The laptop recognizes my phone when I connect it via USB, so I'm wondering if there's some way to get the device to show up.

---

### Post by Vladlenin5000 on 2014-09-22
Turn on USB tethering in your phone after connecting the USB cable. In a moment you should see a new LAN connection. No further steps are needed. Why are you complicating things that couldn't be simpler in the newer Ubuntu versions?

---

