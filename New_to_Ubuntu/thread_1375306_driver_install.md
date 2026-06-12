---
title: "driver install"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by srdente on 2010-01-07
I bought a card reader and on the package it said it had Linux drivers. I looked thru the device manager and didn't see it. I have no idea which files on the cd are the drivers and if I did I don't know how to install them. Ubuntu 9.10 is my system. Any ideas?

---

### Post by howefield on 2010-01-07
Have you attached it to your computer yet ?

You might find it just works.

---

### Post by running_rabbit07 on 2010-01-07
+1 Howefield

---

### Post by Buuntu on 2010-01-07
Look for a README or similar text file in the CD, that might point you in the right direction. 
Have you tried your card reader to see if it works already?  Most things should work without having to manually install drivers in Ubuntu, that's why I ask.

By the way, is this an SD card reader, or what kind of card reader?

---

### Post by tom.swartz07 on 2010-01-07
:lolflag::lolflag:> **howefield said:**
> Have you attached it to your computer yet ?

You might find it just works.

I suppose you have to start somewhere...

In all seriousness, 99.9% of the time, Things will work right from the box without the need for drivers or anything.


Hope it works!

---

### Post by srdente on 2010-01-07
Its a CAC card reader usb for authentication with a smart card. I ran a pcsc scan and it didn't see it.

---

### Post by howefield on 2010-01-07
If your card is any of the ones mentioned on this page, it might help. (Although it doesn't look bang up to date)

[https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

As someone else mentioned, there should be a README or similar on the cd that came with the CAC.

If you are still stuck, post the make/model ect.

---

### Post by srdente on 2010-01-07
Model 111-6
Manf.  Stanley Global Technologies

---

### Post by Captain_tux on 2010-01-07
Do you see it listed when you run **lspci** or **lsusb**?

---

### Post by srdente on 2010-01-07
under lsusb it comes up as:
Bus 001 Device 007: ID 0bda:0165 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Didn't see it in lspci.

---

### Post by sandyd on 2010-01-07
4th post
[http://ubuntuforums.org/archive/index.php/t-457084.html](http://ubuntuforums.org/archive/index.php/t-457084.html)

---

### Post by howefield on 2010-01-07
That's a little out of date, a lot happens in 3 years, especially in linux eg, coolkey is now in the repository.

Might be a tutorial a little more current available.

Just saying.

---

### Post by srdente on 2010-01-07
Thanks to everyone for your help. Tomorrow I am going over Carlee's link and see if their is any useful info that will help.It might send me in the right direction.I do know it a Realtek chipset for usb card reader from my lsusb readout.

---

