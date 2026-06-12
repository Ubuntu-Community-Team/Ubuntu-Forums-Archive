---
title: "hoow do I set up Netgear Wireless Adapter WG111v2"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Dennis56 on 2007-05-26
I have recently started using the Ubuntu OS and I was wondering how would I set up my Netgear Wireless Adapter WG111v2 with Ubuntu?

Thanks in advance,
Dennis

---

### Post by chili555 on 2007-05-26
I think this might be a prism54 device. You can check with the terminal command:```
lsusb
```It should include something like *ISL3887* or similar. If my guesswork is correct, there will be three approaches:
#*sudo modprobe prism54usb.* See if the built-in kernel module works for you.
#Check here: [http://jbnote.free.fr/prism54usb/](http://jbnote.free.fr/prism54usb/)
#ndiswrapper. *sudo apt-get install ndisgtk* and then install the Windows .inf file from your Netgear CD.

Post back if you get stuck.

---

### Post by Jose Catre-Vandis on 2007-05-26
You have some choices:

If you are running Fiesty 7.04, then driver support is built in to the kernel, its a bit dodgy, and you may not get the blue blinking light, but it does work.

If you prefer not to go that way, you can use ndiswrapper which will handle the windows driver for your adapter

The only thing you have to watch for is to be certain you have a V2, very often they were labelled V2 when in fact they were a V1

There are plenty of good howtos on the forum - search on "WG111V2"

---

