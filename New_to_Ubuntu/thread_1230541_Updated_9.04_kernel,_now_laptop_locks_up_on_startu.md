---
title: "Updated 9.04 kernel, now laptop locks up on startup"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by qwerty1105 on 2009-08-03
in training...

I installed fresh dual boot (8.10 & XP) on my laptop (OLD Toshiba Satellite).  I ran that for a while, then upgraded to Jaunty.  Everything works fine.  I then ran various updates and updated the kernel.  Now in grub I have four kernel options at startup.  The only one that boots is 2.6.27-14.  Latest update is 2.6.28-15, which doesn't boot.  It locks up on "pci 0000:00:1e.0 prefetch window", etc...  All the kernels that I have tried do the same, except for the original kernel.  I have a PC Card Wireless adaptor and a usb mouse.  I physically removed them and tried to boot without, to no avail.

Any thoughts?

Thank you

---

### Post by mprince on 2009-08-03
I'd recommend you edit your grub menu so that it only boots with the 2.6.27-14 version.

Follow the directions on this web page. It's about cleaning up the grub menu, but it's the same process. Just remove the references to the later kernels that won't boot.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

Be sure to keep the 'recovery mode' for 2.6.27-14 and the 'memory test' entries.

---

### Post by qwerty1105 on 2009-08-03
What I am doing now is editing the grub menu to boot automatically on the one that works.

What I am trying to figure out is why the updates don't work on my laptop.  Is there a way to find out what is causing it to lock up?  This laptop is a "learning" experience for me and I would like to dig deeper into things if I can.  I am not afraid to break it.  :D

---

