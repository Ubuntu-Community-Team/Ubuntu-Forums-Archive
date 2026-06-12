---
title: "BIOS creates extra instances of ubuntu"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by ja660k on 2009-11-11
Hey, as the title suggests... my BIOS is creating more instances of ubuntu...

like:
Ubuntu 9.04
ubuntu 9.04 (safe mode) *or whatever it is
Ubuntu 9.04
ubuntu 9.04 (safe mode)

other
Windoze
windoze restore

as you can see... ubuntu is listed twice, and i dont have ubuntu instaleld twice?

how can i change this.

---

### Post by luctor on 2009-11-11
This isn't the BIOS but the GRUB bootloader (the program that actually starts operating systems.

Seems that the file /boot/grub/menu.lst is a bit messed up.
Be carefull editing that file, if you mess it up your PC won't boot up anymore.
I suggest installing startupmanager.

[http://packages.ubuntu.com/search?searchon=names&keywords=startupmanager](http://packages.ubuntu.com/search?searchon=names&keywords=startupmanager)

---

### Post by Matt__ on 2009-11-11
what are the kernel version numbers next to the 9.04 entries?
you will get multiple entries as the kernel is updated which can be removed.
easiest way is with [Ubuntu Tweak]("http://ubuntu-tweak.com/downloads").

---

### Post by ad_267 on 2009-11-11
No it's not messed up. It's just that when Ubuntu updates the Linux kernel, it keeps old versions in case there are problems with the new kernel. You can then boot using the old kernels. If you open the Synaptic package manager you can remove the old kernels by removing the old linux-headers and linux-image packages.

---

### Post by 3rdalbum on 2009-11-11
That's perfectly normal. It's not multiple instances of Ubuntu, it's just that you have two kernels installed (you've probably run the Update Manager and it's downloaded a new kernel as an update). It lists the old kernel just in case you have trouble with the new one, although I must say I've never had any kernel trouble.

If you really want to remove the old one, just go into Synaptic Package Manager and get rid of it, and I believe it will be removed from the GRUB screen too.

---

### Post by ja660k on 2009-11-11
is it a good idea to remove this?

---

### Post by coffeecat on 2009-11-11
> **ja660k said:**
> is it a good idea to remove this?

Only when you manage to collect more than 2 kernels. Normally the updated kernels are fully tested before release, but there may still be a problem with obscure combinations of hardware, and this may affect you.

As others have said, the immediately previous kernel should be kept if you experience problems with the newest version.

---

### Post by ad_267 on 2009-11-11
If the current one is running fine, then it's safe to remove all the old ones. Just check all the version numbers before removing to make sure you don't remove your current kernel.

---

