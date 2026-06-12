---
title: "How to Edit Grub?"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by YoungD112 on 2010-03-11
Hello.  With the old grub I knew how to change the order and what shows up on the boot loader, but with grub 2 I'm lost.  Can anybody help me put Windows as my primary OS?  Also, there are about 4 other ubuntu kernels that I don't use, how can I get rid of these to make my boot loading cleaner?

---

### Post by n0dix on 2010-03-11
See the third comment in [this]("http://ubuntuforums.org/showthread.php?t=1418197") link.

---

### Post by audiomick on 2010-03-11
Hallo.
Here is some info
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

In the last link down the page a bit there are instructions about removing old kernels.

I would suggest removing the old kernels first, then editing your grub to how you want it.

It is a good idea to leave at least two kernels on the machine. That way, if something goes wrong with the current kernel (bad update, or whatever), you can still boot into the intact older version.

---

### Post by hhh on 2010-03-11
First get rid of your unwanted kernels, it will make reordering Grub 2 easier. Everything I've ever read recommends having 2 kernels, a new one and one you know works just in case...

[http://ubuntuforums.org/showthread.php?p=8923070#post8923070](http://ubuntuforums.org/showthread.php?p=8923070#post8923070)

Reboot to make sure everything's OK.

Now browse to /boot/grub/grub.cfg and open it in a text editor, just to look at it. Scroll down to the first line that says "menu entry" and count that as zero. Keep counting how many menu entries you have till you get to your Windows entry (so kernel is 0, kernel recovery mode is 1, backup kernel is 2, etc...). With 2 kernels and their recovery modes and the two mem tests, my Windows entry was 6, your's may be different.

Now press F2 on your keyboard, or open a terminal, and enter...
```
gksu gedit /etc/default/grub
```

Right at the top, find the line...
```
GRUB_DEFAULT=0
```and change the number to the number of your Windows entry (again, 6 in my case). Save the file and exit. Open a terminal and run...
```
sudo update-grub
```

Reboot. You should see that the kernel entries are still in the same order but Windows is highlighted by default and will boot if you don't hit a key. Done.

I got these instructions from here...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
... and I'm assuming that the kernels are supposed to stay in order to prevent any errors when you get your next kernel update (but I don't know).

HTH

---

### Post by hhh on 2010-03-11
Dang, good link n0dix, learn something new every day.

---

### Post by n0dix on 2010-03-11
I hope also helps to @YoungD112.

---

### Post by YoungD112 on 2010-03-11
Thanks everybody, everything you suggested worked perfectly

---

