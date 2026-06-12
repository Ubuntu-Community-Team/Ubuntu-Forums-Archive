---
title: "Linksys wusb54gsc on imac / powerpc"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by blenzi on 2006-11-20
After some hours of pain I could finally install wusb54gsc on Dapper using ndiswrapper. But I can't compile ndiswrapper on imac / powerpc:

/home/blenzi/bin/ndiswrapper-1.21/driver/misc_funcs.c:909: warning: ‘__stdcall__’ attribute directive ignored
/home/blenzi/bin/ndiswrapper-1.21/driver/misc_funcs.c:909: warning: ‘regparm’ attribute directive ignored
{standard input}: Assembler messages:
{standard input}:405: Error: Unrecognized opcode: `mov'

I have tried several versions (including 1.28) unsuccesfully. Is there a Mac  alternative for ndiswrapper?

---

### Post by bjd on 2006-11-21
Ndiswrapper probably only works on x86 style cpu's, since it's intended for windows drivers.
You could try my attempt at a native driver for rndis usb wireless lan devices. I have a US robotics usr5421 device, but i think it should also works for linksys wusb54gsc. Works fine for me in access point mode using either WEP or WPA encryption.
Look here: [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)

---

### Post by blenzi on 2006-11-21
I can compile and install it, but when I plug the wireless adapter the system locks. Both my mouse and keyboard are pluged in usb, so maybe this makes things worse (system hangs completely, not just these devices).

---

### Post by bjd on 2006-11-21
Shame it didn't work. I don't see why it would hardlock at the moment..
Did you run clean.sh to remove existing usbnet,cdc_ether and rndis_host modules? They might otherwise conflict with the new ones.
Otherwise i suggest removing my driver for now (remove modules from /lib/modules/<kernel>/extra and sudo depmod -ae)

---

### Post by blenzi on 2006-11-21
Yes, I ran clean.sh. I didn't remove the driver because it's not interfering with my usb devices (keyboard, mouse, flash drive). If you have any anternatives please let me know.

---

### Post by cantormath on 2006-11-21
that card is hell in a box.  I would change cards and forget about Ndiswrapper.](*,)

---

### Post by blenzi on 2006-11-21
Unfortunately that's not an option... RNDIS was suposed to work with wusb54gsc.

---

