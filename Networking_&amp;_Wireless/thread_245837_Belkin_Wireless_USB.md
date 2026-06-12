---
title: "Belkin Wireless USB"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by stifler7 on 2006-08-28
Just wondering if any one can help me out. Been looking through a lot of posts and trying different things, but cant get this USB device to work. Using ndiswrapper. keep getting "invalid driver" tried numerous driver files including XP ones on Disc. Am a complete Noob when in comes to linux, so i hopefully have done something simple wrong, and a quick change will sort it out.

Cheers


P.S its a Belkin USB Wirless G Adaptor F5D7050

---

### Post by stifler7 on 2006-08-29
Bump

---

### Post by Rhubarb on 2006-08-29
I'm a bit of a noob myself, but I have read a fair bit of these forums.  So this could be completely wrong:-

For starters, it's a usb device, and linux tends to prefer PCI / PCI express network cards.  So while ndiswrapper can install the drivers for the network part, it won't install drivers for the USB part of it.

USB was never ment to carry network traffic reliably.  (Please don't flame me RE this, this is just my personal experience).

If you want to guarantee that your wireless connection will work, ... it is a little expensive, get a wireless network bridge, and plug that into your network card in your PC.

---

