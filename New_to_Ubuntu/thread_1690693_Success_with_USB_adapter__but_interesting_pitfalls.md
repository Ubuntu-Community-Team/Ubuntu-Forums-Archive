---
title: "Success with USB adapter  but interesting pitfalls encountered."
date: 2011-02-18
forum: New to Ubuntu
---

### Post by David Proterun on 2011-02-18
THE COMPUTER: 2001 Pentium 4 40GB HD original 256 MB RAM. USB 1.0.
Upgraded. Later added USB 2.0 card and 512 more Ram to 768 RAM total. Ubuntu 10.10

THE DEVICE: A large USB adapter generic with Ralink software disk only US$9.00.
Took me two weeks, Ralink then Realtek drivers, Forum advices.

1. Found that the mystery adapter was really a Realtek 8176. lsusb gave me this info. So forget the software disk and all the installation advice for Ralink. 

2. Try install separate windows computer.  Output"Unknown Device" actually in this case found that the wide adapter was pushing into the USB slot far enough for other computer to note something was there but not far enough to make a connection. When I used a USB extension cable I was able to install on windows computer and further verify Realtek 8176 identity.

3.OK, just download Realtek driver. Nope the one labeled USB driver was not the correct one, it was the CU not the CE driver. Forum advice to the rescue here.

4. OK plug it into the USB 2.0 slot. Nope not that easy.  Finally found that it worked ONLY on the original equipment USB 1.0 slots. Power outputs: The installed USB 2.0 card has an optical mouse attached that works fine. ( removed optical mouse still will not work on USB2.0 card.

Conclusion: Think beyond the usual problems with installing new device.
Hope this is helpful info.

---

