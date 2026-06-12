---
title: "Boot issues"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by harmsc12 on 2009-03-17
My Ubuntu installation is having fits.  I run the installer disk, everything goes smoothly, and after it reboots when it's done, everything seems just fine.  I restart my machine again, Grub doesn't start, and my machine tells me it needs to boot from a system disk.  It's a brand-new machine with a SATA hard drive, and Ubuntu is the only thing on it.
](*,)

---

### Post by Bodsda on 2009-03-17
> **harmsc12 said:**
> My Ubuntu installation is having fits.  I run the installer disk, everything goes smoothly, and after it reboots when it's done, everything seems just fine.  I restart my machine again, Grub doesn't start, and my machine tells me it needs to boot from a system disk.  It's a brand-new machine with a SATA hard drive, and Ubuntu is the only thing on it.
](*,)

Please check your device boot order in your bios, you need to make sure it is set to boot from the hard drive, not from cd or floppy, although that should not be the reason for the message, could you please write down the exact message and tell us it, are there any grub errors? what have you tried?

---

### Post by harmsc12 on 2009-03-17
Grub seems to work fine when I leave the CD in, but without it, I get this:

PCI device listing ...
Bus No. Device No. Func No. Vendor/Device Class Device Class IRQ
0 0 0 10DE 03EA 0500 Memory Controller NA
0 1 1 10DE 03EB 0C05 SMBus Cntrlr 5
0 2 0 10DE 03F1 0C03 USB 1.0/1.1 OHCI Cntrlr 10
0 2 1 10DE 03F2 0C03 USB 2.0 EHCI Cntrlr 11
0 5 0 10DE 03F0 0403 Multimedia Device 10
0 6 0 10DE 03EC 0101 IDE Cntrlr 14
0 8 0 10DE 03F6 0101 IDE Cntrlr 11
0 8 1 10DE 03F6 0101 IDE Cntrlr 10
0 13 0 10DE 03D0 0300 Display Cntrlr 11
1 7 0 1814 0701 0280 USB Cntrlr prog. Interface 5
ACPI Controller 9
Verifying DMI Pool Data........
AMD Data Change...Update New Data to DMI! Update Success
Boot from CD:
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

This is the same screen I got before I installed Ubuntu.  Maybe it's looking for an OS on a nonexistent IDE hard drive and disregarding the one on the SATA drive?  Should I add an IDE hard drive and put Grub on it?

---

### Post by kanikilu on 2009-03-17
Does your BIOS have an "OS install" setting? If so, try turning it off (set it to "finished"). Also, as already suggested, double check that your hard drive is at the top of your boot order list.

---

### Post by harmsc12 on 2009-03-17
The hard drive is the first device, and I did not see an OS Install setting in my BIOS.  I'm going to try something.

---

