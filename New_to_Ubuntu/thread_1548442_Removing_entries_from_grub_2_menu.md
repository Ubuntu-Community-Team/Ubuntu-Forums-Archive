---
title: "Removing entries from grub 2 menu"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Aulex on 2010-08-08
how do u remove entries from grub 2 menu, this is my grub menu

[http://yfrog.com/jkimg4151jj](http://yfrog.com/jkimg4151jj)


now i want to remove the linux 2.6.32-21 kernels and the extra windows option. I would also like to make the grub menu select windows at start up, now i've done this before but i dont remember how. Thanks for the help:popcorn:

---

### Post by Gone fishing on 2010-08-08
Open synaptic System > Administration > Synaptic

and remove linux-image-2.6.32-21

However, it is a good idea to keep the last kernel image so that you have the latest 2

---

### Post by Rubi1200 on 2010-08-08
You also need to remove the linux headers for the image. In total, you will be removing 3 files.

If you wanted to remove the memtest entry (not everyone uses it) you can use this code in the terminal:

```
 sudo chmod -x /etc/grub.d/20_memtest86+
```

---

### Post by Aulex on 2010-08-08
> **Gone fishing said:**
> Open synaptic System > Administration > Synaptic

and remove linux-image-2.6.32-21

However, it is a good idea to keep the last kernel image so that you have the latest 2

i already did that

---

### Post by oldfred on 2010-08-08
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

You can do a total customized menu if you want, but you have to edit several grub files and put most of you boot into 40_custom and/or copy to 06_custom.
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

---

### Post by Gone fishing on 2010-08-09
It should have updated grub when you removed the kernel image, however, sudo update-grub should do the trick

---

### Post by hasanaa on 2010-08-09
you can remove old kernels automatically by using ubuntu tweak.

---

### Post by MartyBuntu on 2010-08-09
> **hasanaa said:**
> you can remove old kernels automatically by using ubuntu tweak.

That's what I use.

---

