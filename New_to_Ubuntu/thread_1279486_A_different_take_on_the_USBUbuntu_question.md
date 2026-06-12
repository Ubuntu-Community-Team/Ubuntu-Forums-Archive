---
title: "A different take on the USB/Ubuntu question"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by jmundinger on 2009-09-30
I had Lenny and Ubuntu installed on an old laptop on which the motherboard is now toast - the connections with the memory chips failed.  I salvaged the hard drive before disposing of the machine.  I have looked at a couple of different threads regarding installing Ubuntu to USB flash drives and USB external hard drives.  Since both Lenny and Ubuntu were running on that hard drive before the motherboard fail, would it still be possible to boot into either of those systems were I to connect that hard drive to another computer with a USB adapter cable and assuming that the other computer has the capability to boot from a USB device?

---

### Post by gordintoronto on 2009-09-30
You should be able to boot from it.  The hardware differences might be an issue.

---

### Post by cariboo on 2009-09-30
If you have grub installed on your external drive, just plug it into a system that will boot from usb and you're ready to go.

The only problem you might have is if you used restricted drivers for you graphics adapter, but that is easily fixed. Most of the drivers you need are included with the kernel so it won't make any difference if the hardware is different.

---

### Post by jmundinger on 2009-09-30
> **cariboo907 said:**
> The only problem you might have is if you used restricted drivers for you graphics adapter, but that is easily fixed. Most of the drivers you need are included with the kernel so it won't make any difference if the hardware is different.

When that hard drive was still in the old laptop, I had installed Debian/Lenny with the on-line installation, after downloading the i386 iso and burning the cd that was necessary to get that installation started.  I installed Ubuntu after burning the cd from the downloaded iso for 9.04.  I had to fiddle with Lenny to get it to recognize the wireless card.  I made no hardware changes in the Ubunto application.

---

