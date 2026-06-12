---
title: "[SOLVED] Did BlueZ just kill my Bluetooth adaptor?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by HyperHacker on 2008-06-12
I don't know if I'm expected to dig through their site to find a place to ask or just post here, as it links to the wiki here, but anyway after I installed BlueZ nothing can see the adaptor, the LED doesn't light up (it was blinking before I installed it), there's no Bluetooth options in the menus or settings, and programs that use Bluetooth (such as the [Wiiuse](http://www.wiiuse.net) example) show the message "hci_get_route: No such device". I even tried plugging it into a Windows machine and a USB charger thinking I'd get a new-hardware-found dialog or at least the LED would blink but no, nothing happens. Even after removing BlueZ and rebooting there's no response. Nothing Bluetooth-related shows up in lshw either.

The one thing that does happen is if I remove the adaptor and plug it in again at the GRUB menu, the computer beeps, as it usually does when you plug in a USB device before an OS has started.

[Edit] Seems like it was physically damaged. Just a crazy coincidence.

---

