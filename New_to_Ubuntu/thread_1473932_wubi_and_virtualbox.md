---
title: "wubi and virtualbox"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by launchy on 2010-05-05
1) if install ubuntu via wubi, is my windows installation going to be infected by viruses? (knowing that linux doesnt need an antivirus and linux is installed inside windows)

2) what is the best linux distro / ubuntu derivative that can run fairly smoothly in virtualbox? (intel celeron 3.33ghz with 1gb ram, win vista 32bit)

---

### Post by natravis on 2010-05-05
1) Windows will not be infected by anything through Ubuntu whether you install it through Wubi or any other way. If your computer already had viruses, they will still be there but Ubuntu will not add anything

2) With those specs, I don't know if any would run well in virtual box. Your best bet would be to just boot from a live CD of any of a number of distros and see what you like. Ubuntu, Fedora, Linux Mint, and slax all have live CDs, to name a few.

---

### Post by sydbat on 2010-05-05
1) I wouldn't install via wubi. It will cause more headaches than it is worth (I know, because I was silly enough to do so with my first Ubuntu install).

If possible, create a separate partition and install cleanly there. Alternately, if you have a second hard drive, install cleanly there.

2) And, as natravis has already stated, I do not think you would have a successful time running anything in virtualbox with your current specs.

---

### Post by launchy on 2010-05-05
> **sydbat said:**
> 1) I wouldn't install via wubi. It will cause more headaches than it is worth (I know, because I was silly enough to do so with my first Ubuntu install).

what kind of headaches did u experience that i might go through using wubi?

---

### Post by wilee-nilee on 2010-05-05
Look through this.
[http://swiss.ubuntuforums.org/tags.php?tag=wubi](http://swiss.ubuntuforums.org/tags.php?tag=wubi)

---

### Post by alzie on 2010-05-05
I'm using a wubi install.  no issues.

Anyhow... If you choose to go with Wubi you won't see the same performance as you would with a full install as Wubi runs Ubuntu in a "virtual disk" in memory.  It's like renting a car to see if you like it vs a test drive from a live CD.

That said, my Wubi install runs nicer on my ancient PC than WinXP.

As Wubi runs Ubuntu on a "virtual disk" I don't think you need to worry about a virus getting in that way.

---

### Post by shae on 2010-05-05
1) If you install Linux through virtual machine or Ubuntu through Wubi, you should not open your computer to additional viruses.  The only possible concern is if you download a file through Ubuntu/Linux that has a virus, then transfer it to Windows and use it there, but then again that could happen with anything.

2) I think Wubi or a Live CD might be a better bet to wet your toes, but I would not completely rule out virualization.  It will probably need to be with a lighter distribution like Lubuntu or Xubuntu as you will not be able to use enough ram.

---

### Post by anewguy on 2010-05-06
I agree with using the LiveCD's as a way to try out the various distributions.  Additionally, I would shy away from a virtual machine for now.  I have used them in the past, and the only way I really liked the performance much was if I had 2 or more processing cores so that I knew at least 1 would basically be dedicated to the VM.  IF you have the resources, then I would create the disk space and install Ubuntu to dual-boot with Windows.

Just my opinion......

Dave ;)

---

