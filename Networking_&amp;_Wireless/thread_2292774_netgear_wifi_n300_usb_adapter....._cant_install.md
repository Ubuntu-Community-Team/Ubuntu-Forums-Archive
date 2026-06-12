---
title: "netgear wifi n300 usb adapter..... cant install"
date: 2015-08-30
forum: Networking &amp; Wireless
---

### Post by Ron_luckey on 2015-08-30
so i am sure this is a simple loose nut at the keyboard ( i am the idiot)  situation how ever i have read several other forums and tried this that and the other and just can not get this thing installed... I live in Oregon USA and if there is anyone that would like to chat with me on phone or text or what ever that would be cool too just want to get this desktop up and running asap... wondering though if the problem is that machine is not connected to internet at all I.E. hardwired... if that is the issue that can be fixed with a relocation of machine and yes i am in idiot but with some patients i can get this lol

---

### Post by chili555 on 2015-08-31
Inexperience doesn't mean idiot. Please don't worry as all of us were beginners once; even me and even Linus!

Let's start by identifying your device. Please insert it in the USB slot and open a terminal Ctrl+Alt+t and run:```
lsusb
```As it suggests, this means, roughly, "**l**i**s**t all the **USB** devices.'

Post the result in your reply. Thanks.

---

### Post by joe184 on 2015-09-16
I also am having this problem. I've followed instructions on other threads and have had no luck getting the WiFi usb to function or be recognized by my pc. The device comes with a resource CD. So I have all the software needed to install it. Just need the stuff to make it work on ubuntu.

Netgear N300 WiFi usb dongle/Adapter (WNA3100)

PC SPECS: 
MFG - Dell
MODEL - GX280
RAM - 2gb 
UBUNTU - 14.04

---

### Post by adamftzptrck on 2015-09-16
did you try to do the above lsusb command to identify the device?
I would also try all of the usb ports, I've found on some laptops that only certain usb ports were disabled (i.e. usb 2.0 or usb 3.0). If you have a desktop have you thought about finding a good pci express wifi adpater?

---

### Post by joe184 on 2015-09-16
> **adamftzptrck said:**
> did you try to do the above lsusb command to identify the device?
I would also try all of the usb ports, I've found on some laptops that only certain usb ports were disabled (i.e. usb 2.0 or usb 3.0). If you have a desktop have you thought about finding a good pci express wifi adpater?

@ Adamftzptrck 

Yes I tried the "lsusb" command and my desktop did not recognize it. I didn't try it on all USB ports. I will try that tonight just to take out that variable. This is an older desktop so it's usb 2.0.  As far as finding a good pci express WiFi adapter, no I haven't gone that direction. I will probably end up going that route since it seems to be the simpler alternative in this  case.

---

### Post by chili555 on 2015-09-16
If it is inserted and it doesn't appear at:```
lsusb
```Then there is nothing we can do. The hardware and driver won't work at all. Sorry.

---

### Post by joe184 on 2015-09-16
> **adamftzptrck said:**
> did you try to do the above lsusb command to identify the device?
I would also try all of the usb ports, I've found on some laptops that only certain usb ports were disabled (i.e. usb 2.0 or usb 3.0). If you have a desktop have you thought about finding a good pci express wifi adpater?

I appreciate the honesty and assistance. Is there a specific PCI wifi adapter that is linux/ubuntu friendly?

---

