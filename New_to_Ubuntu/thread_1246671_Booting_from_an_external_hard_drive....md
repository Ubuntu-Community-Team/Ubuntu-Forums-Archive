---
title: "Booting from an external hard drive..."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by helblaze on 2009-08-22
Seeing as there is no live boot for studio, is there a way to install studio to an external hard drive and not have the OS selection screen show up.  But have it auto boot if the hard drive is plugged into a usb port?.

I'm using a 250gb external.

I'd also like to know, how to boot the OS up through VM ware inside of Vista.

Also can I update drivers on a bootable USB?

---

### Post by MelDJ on 2009-08-22
> **helblaze said:**
> Seeing as there is no live boot for studio, is there a way to install studio to an external hard drive 

Yes. Change your BIOS to boot from external hard disk

---

### Post by oldfred on 2009-08-22
You want your bios to boot from the USB first and then if it is not plugged in boot from the internal drive.
If you have GRUB on the USB drive you can set the timeout to 3 seconds and hidden so you do not see the menu unless you press escape within the 3 seconds.

---

### Post by gn2 on 2009-08-22
Better to use a flash drive as a boot device, they are far more reliable for this role than a mechanical hard drive which may not spin up in time to be detected.

---

