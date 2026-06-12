---
title: "Installation Problem."
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Zanderist on 2010-09-07
I've split my hard drive into two different volumes.

On one of the Volumes I have vista. And the other Ubuntu.

After Installing Ubuntu (from a USB stick), now into the restart phase.

My computer skips right over the choice between ubuntu and vista  going straight into vista.

How do I get the OS choice screen at start up?

I think I might have an idea as to what to do.

---

### Post by Elentir on 2010-09-07
First install Vista, then Ubuntu.

---

### Post by orangeworx on 2010-09-07
you should be able to get into grub by holding shift on boot...
HTH

---

### Post by Rubi1200 on 2010-09-07
You have to highlight the Ubuntu entry by moving the cursor down and then hit Enter otherwise if Vista is the first entry it will default to booting that first.

---

### Post by Zanderist on 2010-09-07
Okay, I have installed vista already.

My problem is that after installing ubuntu afterward, I  cannot select it, I don't see a OS selection screen. It skips straight into windows

On the other hand I can get into ubuntu if I Press F9 at start up and boot from the USB stick.

Before I had it working the way I wanted to (before my hard drive crashed), that time I was using Wubi.

What I'm doing differently this time is that instead of using Wubi, I'm using the USB start up, with a volume set aside for it.

---

### Post by bcbc on 2010-09-07
It seems like the installer put grub on the USB stick you installed from.

So you just need to boot ubuntu and reinstall grub in the place you want it. e.g. boot from your USB stick using F9. This gives you the grub menu you want, and you can select your new ubuntu install and boot it. 

Then just install grub to the internal drive: 
```
sudo grub-install /dev/sda
```

This assumes that: your drive is /dev/sda, and that you did in fact boot ubuntu on the same hard drive as windows. If you are in doubt, then boot ubuntu and post the results of the [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

PS it will be different  to the wubi install because you won't see the windows boot manager first (offering windows or ubuntu). You'll just see the grub menu. If you want to try and boot ubuntu from windows you need something like easybcd. (Haven't used it myself).

---

