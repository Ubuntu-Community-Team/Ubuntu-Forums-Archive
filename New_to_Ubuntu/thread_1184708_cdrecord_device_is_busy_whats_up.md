---
title: "cdrecord device is busy whats up?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-06-11
In my script I tell it do cdrecord a file, it doesnt work and says the device is busy will retry in 1 sec.

but if I do it out of a script in a terminal it works fight I believe.

Any suggestions advice?

its a iso image that I am trying to burn to a blank DVD

---

### Post by ericeclifford on 2009-06-11
I do not know whats wrong it, but it saids device or resource is busy anyone get this?

I have a iso image and I am trying to find the command on how it will burn it.

---

### Post by NightwishFan on 2009-06-11
You can burn .iso images using Brasero, which is installed by default. I believe in GNOME you can right click and tell the iso image to burn.

---

### Post by Johan-Steyn on 2009-06-11
Hi,

Have to agree with NightwishFan. Brasero Disc Burner is to Linux, what Nero is to Windows.

Go to Applications>Sound & Video to find it.

Regards,

JS

---

### Post by ericeclifford on 2009-06-11
> **NightwishFan said:**
> You can burn .iso images using Brasero, which is installed by default. I believe in GNOME you can right click and tell the iso image to burn.

No I need to do it from my script.

No GUI only command line.

---

### Post by unutbu on 2009-06-11
Have you tried growisofs?

[http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line](http://www.debuntu.org/2006/06/03/61-how-to-burn-dvds-from-the-command-line)

See the comment at the end for how to burn an iso instead of a directory. (And if your CD-drive is /dev/cdrom, then change /dev/hda to /dev/cdrom).

---

### Post by ericeclifford on 2009-06-11
Ok i got two dvd rw roms, is there no command line to cdrecord filename.iso dev=dev/something


i mean that is what I was looking for :( cdrecord is for burning right?

---

