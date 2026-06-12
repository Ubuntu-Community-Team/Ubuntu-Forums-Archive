---
title: "pc will not boot from CD/DVD"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by radelster on 2009-01-23
Trying to boot from drive.  System prompts - Boot from cd...
I press Y and enter, nothing happens.
Eventually will come back with another prompt
Press any key to boot from cd/dvd.
I press any key, then I see the countdown from GRUB starting Ubuntu.

I have went into my BIOS and changed the boot sequence to only boot from CD drive - same results.

I changed BIOS and REMOVED THE HARD DRIVE, but it still goes into Ubuntu.

Can anyone please tell me what setting it is, to make the PC boot from the CD drive??

Thanks

---

### Post by Garyhans on 2009-01-23
If you get the grub menu.. try F4 and choose.. safe graphics mode...

---

### Post by taurus on 2009-01-23
Is your CD/DVD even a bootable disc?  What are you trying to boot from the CD/DVD?

---

### Post by radelster on 2009-01-23
actually (gulp) trying to load windows 7 on the pc.

Or windows XP (which I KNOW is a bootable disc).

I get to the 
press ESC to enter GRUB menu, and then a countdown from like 2

I press ESC repeatedly, then it continues the boot into Ubuntu.

---

### Post by taurus on 2009-01-23
If you see the GRUB menu (3 seconds count down), it's a little too late.  It should boot your disc first, if you've changed the option in the BIOS to boot from CD/DVD first.  See if you can boot the same disc with another computer.

---

### Post by radelster on 2009-01-23
> **taurus said:**
> If you see the GRUB menu (3 seconds count down), it's a little too late.  It should boot your disc first, if you've changed the option in the BIOS to boot from CD/DVD first.  See if you can boot the same disc with another computer.

The XP disc I know works, as I installed it on the PC I am typing to you now from.


Anyone else have any idea how to shoot the grub??

---

### Post by radelster on 2009-01-24
ANYONE???

Please help me remove ubuntu/grub from my computer:oops::oops::oops:

---

### Post by diablo75 on 2009-01-24
If you've changed the BIOS's booting priority (looks like you have), perhaps there's a Function-Key you can press to bring up a boot menu.  On some PC's it's F12.  This might bring up a list that display possible devices for it to check and see if something can be booted from it.

If you're comfortable with opening up your PC, check to see if the data cable that is attached to your CD-ROM is the same cable attached to your hard drive.  If it is, here a drastic "rule out all possibilities" test:  Detach the data and power cables from your hard drive, then turn the PC back on to see if it will boot from the CD drive now.  Re-attach the hard drive and try it again to see if it works or fails.

---

