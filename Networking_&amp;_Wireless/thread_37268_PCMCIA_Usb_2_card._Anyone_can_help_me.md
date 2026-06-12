---
title: "PCMCIA Usb 2 card. Anyone can help me?"
date: 2005-05-26
forum: Networking &amp; Wireless
---

### Post by fparri on 2005-05-26
I have one. From /var/log/messages it seems it's working but I can't access the contents of a pen drive I insert into it. Do you know where I can find it in order to mount it?

---

### Post by Jussi Kukkonen on 2005-05-27
To make sure the pcmcia card is working as expected, check the result of *lspci*: AFAIK you should have two "CardBus Bridge" devices (if it's a 2-port card). Also, *lsusb* should show the hubs.

If the hubs seem to work, plug the usb drive in and see what *dmesg* says. You should find the correct device name somewhere there.

---

