---
title: "WD My Book usb 3.0 hard disk not detected with ubuntu 10.10"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by thej22 on 2011-03-19
Hi All
    
      I was trying to check Western Digital(WD)My Book3.0 hard disk on my system.I have a NEC 3.0 PCIe card.
      System has been configured such that it doesn't load the xhci driver while booting as it has been disabled for other purpose.So i manually loaded the xhci driver after system booted using insmod xhci-hcd.ko.

      But i don't see any WDD being detected.Is this the right way to go about or have i missed out on something ??.. 

when i give lspci i get this:
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

I have attached the kern.log for xhci module being loaded.


Regards

---

### Post by quirks on 2011-03-19
I don't have a USB3 drive, so I may not be of much help here, but have you tried unplugging and replugging the drive after loading of the xhci module? Does it say anything in the kernel log, when you plug the drive in?

---

### Post by RBLevin on 2011-03-19
If the drive is plugged in to a USB hub, plug it in directly to the PC. See if that changes things.

---

### Post by thej22 on 2011-03-20
I haven't checked by unplugging and plugging after i load the xhci driver module.Have to try it out.But when i plug WD My Book 3.0 in a usb2.0 port it does get detected as a usb2.0 device.

---

### Post by nrabett on 2011-04-05
Same drive, same problem. Gigabyte MoBo, Ubuntu 10.04.

---

### Post by TeoBigusGeekus on 2011-04-05
Can you post us the output of 
```
lsusb
```
before and after you plug in the drive?

---

### Post by nrabett on 2011-04-05
The problem actually solved itself after some time. Perhaps it was booting once into Windows (dual boot machine) which did it.

---

