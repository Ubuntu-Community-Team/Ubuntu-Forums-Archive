---
title: "LiveCD"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by DucksAndDolphins on 2009-01-17
so i have the live cd for both Ubuntu Intrepid and UbuntuStudio (which i plan to install as well). But when i enter either of the disks, i just get a list of files and programs which wont open to provide some sort of installation process.

help??

---

### Post by igknighted on 2009-01-17
You should reboot and the CD will load on bootup, you don't run it from within windows.

---

### Post by DucksAndDolphins on 2009-01-17
im in ubuntu right now (im looking to reinstall).

should i still just run it from boot up?

---

### Post by drs305 on 2009-01-17
If it doesn't start on rebooting, make sure your system's BIOS is set to first boot from CD/DVD. You usually can enter the BIOS setup right after startup by pressing a specific key such as ESC or the DELETE key - each system has it's own key to invoke the BIOS setup procedure. Once into the BIOS setup, look for Boot Options.

In answer to the question posed as I wrote the above, if you are seeking to completely wipe your old installation and reinstall from the beginning, the answer is yes. Reinsert the LiveCD and reboot or if you have already booted with the LiveCD and have the "Install" CD icon, you can just click on that to start a new installation.

---

### Post by igknighted on 2009-01-17
> **DucksAndDolphins said:**
> im in ubuntu right now (im looking to reinstall).

should i still just run it from boot up?

Yes, the CD needs to boot to its own environment, it cannot run from an existing install.

---

### Post by DucksAndDolphins on 2009-01-17
okay well i left the cd in while i booted up, and i heard it load and the screen stayed darkened for longer than usual..i selected ubuntu from the os-choose menu and then pressed ESC and got the menu containing the regular ubuntu, the recovery mode, the memtest, and several other listings.

i couldnt find the boot options.

---

### Post by igknighted on 2009-01-17
Set your BIOS (the screen before grub) to boot to CD first.  Sounds like your computer booted straight to the hard drive.  You should get a menu that pops up asking you to select a language first thing.

---

### Post by DucksAndDolphins on 2009-01-17
yeah ive never gotten a menu asking me to select a language. is there any way i can set BIOS to boot off the CD from my current desktop?

oh, and i installed off of WUBI the first time, if that has anything to do with the problem.

---

### Post by igknighted on 2009-01-17
> **DucksAndDolphins said:**
> yeah ive never gotten a menu asking me to select a language. is there any way i can set BIOS to boot off the CD from my current desktop?

oh, and i installed off of WUBI the first time, if that has anything to do with the problem.

No, you need to do that from the BIOS menu.  Before you get grub (or windows) there should be a screen the shows up with some sort of logo.  Somewhere on that screen it should give you a key to hit (usually f2 or delete) to get to a menu, where you can set various things (including boot device order).  Be careful what you change here, some of the options could render your system unbootable, so only change the boot device order.

---

### Post by DucksAndDolphins on 2009-01-17
alright, i know what you mean.

ill report back in a bit.

---

