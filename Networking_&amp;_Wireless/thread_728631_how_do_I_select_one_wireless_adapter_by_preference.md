---
title: "how do I select one wireless adapter by preference?"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by DouglasK on 2008-03-19
Is there a way to get the gnome networkmanager to prefer one wireless adapter over another?

My laptop has a Wireless G broadcom built in which works ok at 54Mbps and I use an external Linksys WUSB300N USB wireless N adapter (I normally get 270 Mbps) which is great for accessing my network drives.  both adapters use ndiswrapper to run.

Gutsy (7.10) prefers to use the internal adapter.  To use the USB adapter, I need to manually tell it to switch to it on every boot.

Is there any way to get the network manager applet to prefer the USB adapter?

~~Douglas

---

### Post by uberlube on 2008-03-19
You could always blacklist (or comment out) the broadcom until you want to use it again. Im not completely sure how to do this but I'm pretty sure this is the route you should take.

---

### Post by DouglasK on 2008-03-19
True, I could disable the driver in /etc/ndiswrapper....

Thing is that occasionally I won't use the USB adapter if I'm just going online for a few moments...

Ideally I'd like it to prefer the wireless USB and fall back to the internal one.

The internal one shows up as eth1, the wireless usb as wlan2.  

~~Douglas

---

