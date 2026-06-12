---
title: "USB and card reader dosn't work with SATA hard drive"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by jamesrfla on 2008-12-27
I have Ubuntu 8.04 on a HP Media Center m7160n Desktop PC and I can't seem to get the USB or the card reader to work on it. I currently have a SATA hard drive in it and to run Ubuntu I have to add acpi=off to the kernel. I try another SATA drive and I still have to add acpi=off and USB and the card reader still doesn't work. I can add any IDE hard drive and everything will work. I tried lsusb and nothing came up when I was using the SATA drive. I also tried Ubuntu 8.10 and no luck. Why won't USB and the card reader work with a SATA hard drive? :confused:

---

### Post by cmnorton on 2008-12-27
This sounds like an interrupt problem. You can check the output of /proc/devices to check to which interrupts your hardware is assigned. Did you add SATA support with a PCI card, or was SATA built in?

You may have a combination job of checking to see where the interrupts should be and then checking your BIOS to see if you can change where USB interrupts. I'd be more likely to mess with that than your SATA interrupt.

---

### Post by ranch hand on 2008-12-27
I don't think that this is a SATA problem.  I run on a SATA box with no problems.

This may have to do with your bios settings or your mother board.

---

### Post by jamesrfla on 2008-12-27
The SATA is built in. Hear is the /proc/devices/ [http://pastebin.com/m6e5aef25](http://pastebin.com/m6e5aef25) I checked the BOIS and found nothing that would help me. Everything else will work with a IDE hard drive but not a SATA hard drive. Could it be because of the acpi=off I have to add when I use a SATA drive. Also I think I was trying to install windows on this at one time but I had no luck because it couldn't find the hard drive. RAID driver or something?

---

### Post by jamesrfla on 2008-12-30
It turns out it is a interrupt problem. Hear is the output of my dmidecode [http://pastebin.com/m57391673](http://pastebin.com/m57391673) Hear is the output of dmesg [http://pastebin.com/m44d94dc6](http://pastebin.com/m44d94dc6) Once again I don't have any options in my BIOS to change the interrupts

---

### Post by ajmorris on 2008-12-30
> **jamesrfla said:**
> It turns out it is a interrupt problem. Hear is the output of my dmidecode [http://pastebin.com/m57391673](http://pastebin.com/m57391673) Hear is the output of dmesg [http://pastebin.com/m44d94dc6](http://pastebin.com/m44d94dc6) Once again I don't have any options in my BIOS to change the interrupts

Yep, that is indeed an interrupt error... try appending this to the 'kernel' line in /boot/grub/menu.lst :

```
pci=biosirq
```


AJ

---

### Post by jamesrfla on 2008-12-31
I added pci=biosirq to my kernel. I did find a I/O device configuration in my BIOS but I could only change the Interrupt for my Parallel Port. I changed it but no luck. I even disabled the port. I also changed my Onboard PATA/SATA Configuration to Combined Mode from Enhanced Mode. Nothing seemed to help. I will try to update my BIOS today and see if I get more IRQ options.

---

