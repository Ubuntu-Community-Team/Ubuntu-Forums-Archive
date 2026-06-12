---
title: "How to enable a embedded evdo card?"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by theb on 2007-06-16
Hi,
I got Feisty running on a Vaio TXN25N, so far soo good but I want to try and get the embedded evdo to work.  I have a sprint novatel U720 usb evdo modem that I have gotten to work pretty well.  I was told that the embedded evdo modem was the same mini-pci as the U720 so the drivers should be the same.

My question is: how would I go about to enable the embedded evdo mini-pci?  Is there something like 'device manager' in linux that I can go to see everything attached, hardware wise?

If anyone can help, be great.

Theb

---

### Post by _DjScrew_ on 2007-06-18
First thing to check would be to see if it's enabled in bios.. and then in terminal type "lspci" and see if the device is there.

---

