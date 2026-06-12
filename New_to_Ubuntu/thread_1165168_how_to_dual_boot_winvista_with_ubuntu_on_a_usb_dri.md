---
title: "how to dual boot winvista with ubuntu on a usb drive?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by mhguda on 2009-05-20
I recently installed ubuntu 9.04 on a 60 GB external HD which connects via USB. I did this using my eeepc and it worked perfectly; however I had some problems with touting that drive around so went for a smaller flashdrive.
The 60 GB was still sitting around so I wanted to try the following: on another laptop, which has windows vista installed on it, boot from this 60GB USB as a dual boot option. I used easybcd to add it as a boot option, and it seemed to be added successfully to the bcd. But when I rebooted my machine, it booted right into windows, not showing any boot menu, and when I looked at the bcd, the ubuntu option was gone. Am I doing something wrong?

---

### Post by LoloftheRings on 2009-05-20
What about installing Ubuntu on the USB drive and also installing GRUB (the default bootloader) on the USB drive. Then, in your bios set USB drives prior to internal hard drive for boot priority.
When the usb is attached, it will boot into grub, otherwise Windows!

At least.. that's the theory.

Good luck

---

