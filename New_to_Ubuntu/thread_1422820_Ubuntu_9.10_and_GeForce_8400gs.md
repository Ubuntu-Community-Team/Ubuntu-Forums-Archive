---
title: "Ubuntu 9.10 and GeForce 8400gs"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by oxygenfarm on 2010-03-05
After I installed the GeForce card and got a new Gateway LCD monitor, Ubuntu will not boot from live CD or install. The process starts, then aborts.
I've been using a DVI cable: is this the problem? Or is Ubuntu allergic to GeForce?

---

### Post by PRC09 on 2010-03-06
I have the same card and it works fine with a standard vga cable.I havent tried the dvi tho.Using a EMachines 19 inch HD LCD monitor......

---

### Post by 3rdalbum on 2010-03-06
When you say "it won't boot", what exactly happens? Does it freeze during boot, are there any messages on screen?

---

### Post by oxygenfarm on 2010-03-06
The CD will run for a few minutes, with a logo showing, then stop running w/o further activity.

---

### Post by oxygenfarm on 2010-03-06
Thanks for the hint!
I removed the DVI cable and used only VGA and the live CD worked....
...but when I tried to install Ubuntu there was a message 'fatal error with GRUB' and now on reboot I see a GRUB error 17.
Perhaps an old GRUB entry is preventing a new entry?

---

### Post by coffeecat on 2010-03-06
First up: I have a GeForce 8400GS card connected to my 24" BenQ monitor through a DVI cable and Karmic (and Jaunty and Lucid) boot up just fine from both the live CD and my hard disk installations.

It sounds to me as if you may have a dud CD or corrupted ISO download. Check the md5sum of your ISO first. If that's OK, burn a new CD at a low speed (preferably not more than x4) and try again.

By the way, error 17 sounds like a legacy grub error but Karmic comes with grub2. Do you already have something on your machine? Perhaps you could give us some more details.

---

