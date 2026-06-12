---
title: "How To Boot To USB Drive"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by TheAJGman on 2011-03-02
How do you boot to a usb drive in ubuntu 10.04 64bit. im trying to boot to a home made chromium os build if that helps.
also how do you update grub so it doesn't show my old Ubuntu boot options

---

### Post by jeremyjjbrown on 2011-03-02
You don't boot to any volume in Ubuntu.

You can use your BIOS to boot to a USB drive.

Upon startup follow the prompt to enter Setup by pressing the Del, F8, etc key.

You then edit the Boot Priority list an put USB above the Optical and HD. Then at startup your BIOS will check for bootable USB first and load from it if present.

If you screw something up there should be a restore defaults option in you Bios Setup.

Good Luck!

---

### Post by ianc1 on 2011-03-02
Your PC will usually say some comment on the first screen it show on startup to press ..... to enter Bios.  On mine its F2.

As jeremyjbrown says change the boot order which will be under one of the bios screens.  I've set mine to USB, CD, Hard drive.  Be wary though as some laptops only have a set number of USB ports from which you can boot.  On mine an Advent only the two only the left side can boot the machine.  The one on the right hand side cannot.  Whats worse, depending on the age of the machine, it may not be an option.

---

### Post by TheAJGman on 2011-03-02
ok thanks

---

