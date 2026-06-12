---
title: "Windows USB Drivers in Ubuntu?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by abeisgreat on 2009-01-22
I have this odd USB cable I need to get drivers for in linux, I have several windows drivers (98, XP, 2k, versions of the drivers), I need to know if its possible to install these drivers under linux, the issue is they arent installers, just some dlls and sys files.

Thanks
Abe

---

### Post by 2hot6ft2 on 2009-01-22
> **abeisgreat said:**
> I have this odd USB cable I need to get drivers for in linux, I have several windows drivers (98, XP, 2k, versions of the drivers), I need to know if its possible to install these drivers under linux, the issue is they arent installers, just some dlls and sys files.

Thanks
Abe
Maybe in wine but linux doesn't use dll's or sys files. Try just plugging it in and see if it works out of the box.

---

### Post by emarkd on 2009-01-22
what sort of hardware is at the end of the cable?

---

### Post by abeisgreat on 2009-01-22
> **2hot6ft2 said:**
> Maybe in wine but linux doesn't use dll's or sys files. Try just plugging it in and see if it works out of the box.

Well duh, sorry I pry sounded a little dumb. I tried out of the box, I tried playing around with wine, no luck, im just curious if there is a good way to manually install drivers in wine

---

### Post by handydan918 on 2009-01-22
The real question is this:

What is the device REALLY?

'Cause it ain't just a cable if it needs drivers....

---

### Post by emarkd on 2009-01-22
wine is basically just a collection of libraries.  it can't run drivers.  and you don't sound dumb so no worries.

---

### Post by Frak on 2009-01-22
I too would like to know exactly WHAT you are trying to connect.

---

### Post by abeisgreat on 2009-01-22
Its a EZFA linker cable for a GBA flash cart

---

### Post by handydan918 on 2009-01-23
A quick google shows this to be gameboy related hardware/software for Windows. 
Doubt it can be made to work with Linux, but good luck.

---

### Post by ozbris on 2011-09-03
I realise this is an old thread, but I also was thinking about the same thing - I have bought one of these USB-Ethernet server hubs.. it basically lets you have a USB device (or multiples via a 4 port hub) on your LAN, then with this windows driver software you can map to them as if they were locally connected.

The device is this one:

[http://www.win-star.com/eshop/goods.php?id=92](http://www.win-star.com/eshop/goods.php?id=92)

The docs say you can use OSX bonjour to find a connected LPR printer.. but I specifically want to use it to access a USB storage HD across the LAN.

Any clues?

Alex

---

### Post by Mark Phelps on 2011-09-04
With the rare exception of NDISwrapper (used for networking), Windows drivers do NOT work in Linux. So, there's no point in asking about any specific Windows driver software.

---

