---
title: "Booting from external USB drive when Guardian Edge installed main drive"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by MiTavis on 2009-10-15
I tried to install Ubuntu 8.10 on an external USB SATA drive. The installation appeared to work and I was able to boot into the drive. However, when I went back to boot into windows XP on my main drive, I just hung. It appears that the install placed a boot loader on my internal drive with a pointer to the external drive. Since my main harddrive is encrypted with guardian edge, I had overwritten some critical files. My IT folks spent several days recoving the harddrive. I tried again but this time I removed the internal hard drive. The install did work this time and all I have to do is adjust the BIOS to boot from the external drive before attempting the internal drive.
 
Is there any way to do this without removing the internal drive?

---

### Post by LewRockwell on 2009-10-15
set your machine up to boot first from USB devices and put the bootloader on the external drive

.

---

### Post by MiTavis on 2009-10-16
Actually, I seem to recall that the external drive was set to boot first when I did the install. At this point, I would be concerned with trying again with the machine that I did this on. HP Compaq nc6000. Note that if you have more than one external USB drive plugged in, the system is confused on which one to try and boot from.

---

### Post by Radioman991 on 2009-10-16
Don't feel bad.

I did the same thing...clobbered my Winders MBR on the company encrypted drive.  The next time I pulled the drive out (a laptop), and on my home box, I pulled the power cord.  Yeah it's a small pain, but cheap insurance

---

