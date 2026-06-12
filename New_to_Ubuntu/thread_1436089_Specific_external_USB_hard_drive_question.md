---
title: "Specific external USB hard drive question"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by lpmb on 2010-03-22
Hi

I removed my xp hard drive completely from my laptop and installed 9.10 directly onto a fresh 2.5" drive.   

That 9.10 drive works perfectly when installed in the HD slot.  However when I put this drive in an external HD enclosure (USB) the boot fails, with or without the xp drive installed in the machine. 

The bios is set to boot from USB first and does so successfully with an separate USB flash drive ubuntu install every time (with or without xp drive in place). I can't understand why a fully functioning HD boots from the internal slot but not as a USB external drive.

---

### Post by skatinjj on 2010-03-22
Do you get an error or does it just skip the drive completely during boot?

---

### Post by Doctor Mike on 2010-03-22
> **lpmb said:**
> Hi

I removed my xp hard drive completely from my laptop and installed 9.10 directly onto a fresh 2.5" drive.   

That 9.10 drive works perfectly when installed in the HD slot.  However when I put this drive in an external HD enclosure (USB) the boot fails, with or without the xp drive installed in the machine. 

The bios is set to boot from USB first and does so successfully with an separate USB flash drive ubuntu install every time (with or without xp drive in place). I can't understand why a fully functioning HD boots from the internal slot but not as a USB external drive.
The grub boot loader is probably looking for the wrong type of drive/loction to find startup files. You could try to repair the grub using a Super Grub live cd with 9.10 in the usb possition.

[http://en.kioskea.net/faq/4313-super-grub-disk-live-cd](http://en.kioskea.net/faq/4313-super-grub-disk-live-cd)

See repairing grub on linked page.

---

### Post by undecim on 2010-03-22
If you have another HD in the internal slot, that will mess up grub.

---

### Post by lpmb on 2010-03-23
> **undecim said:**
> If you have another HD in the internal slot, that will mess up grub.


Hi   I've fixed the issue by doing an install a newly purchased external HD and ensuring that grub was installed on the external drive during the initial installation process.  (why this isn't the default I'll never know - what's the point of installing Ubuntu if you can't boot from it???)  I suspect that may have been my problem but I'll never know because I'm using the other drive as a software vault for Aperture 3 now!

Are you sure your comment is correct?  I'm running Ubuntu off an external HD now with no errors, with the original HD drive in situ.   I don't think the presence of an internal HD should cause problems if the BIOS is set to boot from the USB first?

LPMB.

---

