---
title: "Totally Locked Out. I NEED help!"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by wsihlis on 2010-11-16
My computer (HP, dual booting Win 7, pretty standard stuff) has gone from running 10.04 LTS totally stably to completely locking me out. I cannot get past the Busybox shell if I try to boot from the GRUB 1.98 (I think that is 2?), in either Linux 2.6.32-25 or Linux 2.6.32-25 (recovery mode), they both get the same error message saying that the "target filesystem doesn't have /sbin/init." Then the Busybox comes up, and I am stuck with an (initramfs) prompt.
Interestingly, if I boot using Linux 2.6.32-24, or or Linux 2.6.32-24 (recovery mode)I get a different message, saying that "udevadm trigger is not permitted while udev in unconfigured", then a message saying it gave up waiting, then an Alert! and I get kicked down to the Busybox shell.
I have been trying to get this going all night, so I have tried the LiveCD. It won't load. When I boot with the CD in, it gets to a Ubuntu logo with the 5 dots, then there. Pressing a button shows the progress, first that the CD failed due to an unknown user ID, then it tries to boot, and dies on two nonexistant files.
If anybody knows anything that I am missing, I would love you forever. I know how computers work, but I am just terribly inexperienced with command line, so any of those instructions are going to have to be kindergarten. 
I want to believe in Open-source! Don't let me down!

---

### Post by ironic.demise on 2010-11-16
Sounds to me like it's an actual hardware problem?
 
Can you boot Win7 or another Distro cd?
 
Can you get to a command line, if you can you might be able to see if those files are there or not, and if not replace them.

---

### Post by sky_ceiling on 2010-11-16
mmm you sure about that? sounds more like a corrupt bootloader.

Boot into a LiveCD and type in terminal

sudo install-grub /dev/sda

or something like that ;)

Alternatively: Just reinstall

---

### Post by deconstrained on 2010-11-16
If you can't even boot to a CD then it is probably a hardware issue, though I'd double-check the settings in BIOS before anything else (especially the boot/IDE/SATA device settings). A good first thing to try would be the "load optimized defaults" option that is common to so many motherbaords.

If all else fails, try reflashing the motherboard's firmware with a vendor-supplied utility in Windows, or if you can't even boot into Windows, clear CMOS;
[http://pcsupport.about.com/od/fixtheproblem/tp/clearcmos.htm](http://pcsupport.about.com/od/fixtheproblem/tp/clearcmos.htm)
If your computer's a laptop, however, I'd advise against opening your computer up to clear CMOS, because that would most likely void the warranty.

If after all these things you still cannot boot to Ubuntu, a live CD, OR Windows, **then** you have an excuse to go ballistic.

---

