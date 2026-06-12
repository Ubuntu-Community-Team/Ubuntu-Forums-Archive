---
title: "WPC54G Notebook Adapter"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by JoeTux on 2007-08-30
I'm going to be using a WPC54G Notebook Adapter with Ubuntu Feisty to connect to a Linksys Wireless G (WAP54G) Access Point will that connection work without any extra effort once plugged in? Or will I have to manually configure it with the CLI and if so how will I have to go about doing that?

---

### Post by bmartin on 2007-08-31
Mostly likely, it will **not** be plug-and-play. There are multiple versions of the card. If it's a Broadcom chipset, I recommend you use [this thread]("http://ubuntuforums.org/showthread.php?t=405990"). You can check what the chipset is by using **lsusb** at the CLI (if it's a USB device) or lspci (if it's not a USB device).

---

