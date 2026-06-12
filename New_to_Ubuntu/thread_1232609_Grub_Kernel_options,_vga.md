---
title: "Grub Kernel options, vga"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-08-05
So I'm trying to set my boot options for the kernel in grub via the vga=0x791 thing.

0x369 is the code for 1680x1050 24 bit.  I put the option in menu.lst, but on reboot, the stupid thing says it's not supported.  It then gives me a list of options.  One of the options is 369.  I type it in and it works fine then.

So what's the deal here?  It works whenever I have to manually input the same number, but doesn't work from the grub file?

---

### Post by CryptiniteDemon on 2009-08-05
Nevermind.  I'm an idiot.  I kept putting in 869 instead of 369. Don't ask me how I did this 6 times, I just did.

---

### Post by theonhighgod on 2009-08-09
> **CryptiniteDemon said:**
> Nevermind.  I'm an idiot.  I kept putting in 869 instead of 369. Don't ask me how I did this 6 times, I just did.

I've managed similar things, you could try startupmanager it can help in these situations, give it a try.....

---

