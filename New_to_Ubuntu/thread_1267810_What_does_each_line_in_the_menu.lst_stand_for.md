---
title: "What does each line in the menu.lst stand for?"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by tonysonney on 2009-09-16
```
title           Ubuntu 8.04.2, kernel 2.6.30.6
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.30.6 root=UUID=3234321-9a0c-bcadaa-e8b3a ro quiet splash
initrd          /boot/initrd.img-2.6.30.6
quiet
```

        I I know title means what should be shown at boot up?  What are the rest? I assume 'ro' means read only. What is quet and splash? Thanks in advance

Tony

---

### Post by mo0nykit on 2009-09-16
Hello! I'm no expert, but I'll give it a try

**root** indicates which storage device the boot loader should look into for the OS
**kernel** is the path to the compressed kernel (hence the name vmlinu**z**, with a **z**)
**initrd** is the path to the ramdisk (i can't really explain its role in the boot-up process)

I hope that helps :)

---

### Post by Sub101 on 2009-09-16
And quiet and splash mean, it will show Usplash on bootup rather than text.

---

### Post by ajgreeny on 2009-09-16
If you just remove the word "quiet" from the line you will still get the splash, together with a minimal text output, which some people prefer.

---

### Post by Paqman on 2009-09-16
If you're really interested in learning how the nitty-gritty of Grub works, i'd chill for a few weeks. The new version that will be shipped with Karmic is quite different. No point in stuffing your head with learnings that'll be useless in a few weeks time! :)

Having said that, the actual question you asked is common to both, they're just found in different files.

---

### Post by tonysonney on 2009-09-16
Hmm Thanks guys. But do any of you know what is meant by ramdisk? And the grub and menu.lst is universal for all linux. Isnt it?

---

### Post by mo0nykit on 2009-09-16
**@tonysonney**
A little history :) LILO (LInux LOader) was used before GRUB (GRand Unified Bootloader). But today GRUB is intended to eventually completely replace LILO. As for **ramdisk**, someone else might be able to explain :)

---

### Post by LewRockwell on 2009-09-16
> **mo0nykit said:**
> **@tonysonney**
A little history :) LILO (LInux LOader) was used before GRUB (GRand Unified Bootloader). But today GRUB is intended to eventually completely replace LILO. As for **ramdisk**, someone else might be able to explain :)

Search Engine 101:

key in "wiki" and "ramdisk" and press enter

[http://en.wikipedia.org/wiki/RAM_disk](http://en.wikipedia.org/wiki/RAM_disk)

.

---

### Post by LewRockwell on 2009-09-16
> **Paqman said:**
> If you're really interested in learning how the nitty-gritty of Grub works, i'd chill for a few weeks. The new version that will be shipped with Karmic is quite different. No point in stuffing your head with learnings that'll be useless in a few weeks time! :)

Having said that, the actual question you asked is common to both, they're just found in different files.

True, Ubuntu 9.10 Karmic Koala will be released with a new grubloader

However, it is false that the old grubloader will somehow evaporate from hundreds of millions of fully functioning machines all across the globe

Search Engine 101:

key "wiki" and "grubloader" and press enter

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

.

---

### Post by drs305 on 2009-09-16
Grub 2 will not automatically replace Grub (legacy) on updates. It will only be installed by default on clean installs in Karmic. 

There is a link in my signature line to an introduction to Grub 2.

---

### Post by Paqman on 2009-09-16
> **drs305 said:**
> Grub 2 will not automatically replace Grub (legacy) on updates. It will only be installed by default on clean installs in Karmic. 

True, my apologies if I freaked anyone out. Should have been clearer about that.

---

### Post by tonysonney on 2009-09-17
Thank you all very much! That was a lot of info!

Tony

---

### Post by mo0nykit on 2009-09-17
**@tonysonney**
You're always welcome! If you believe your question has been answered, kindly **mark this thread as solved**, using the Thread Tools. You can do this for threads that you start :D

---

### Post by tonysonney on 2009-09-17
Will do.. I did not know that I can close a thread as solved. Good to know about that.
Cheers,
Tony

---

