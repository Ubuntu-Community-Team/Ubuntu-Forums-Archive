---
title: "Ubuntu dual boot with other distro's"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by JoePublic9 on 2009-06-16
Greetings,
  I have been using Ubuntu for about 8 months now and have long since removed windows from my machine. However, I noticed that Ubuntu uses very little space. I thought I would take that space and try some other distro's.
Now, I know that some will suggest Virtualbox but I would rather try a real install. Anyway, I have two questions that I can think of before I start.
 First, my hd.  I have Ubuntu on an extended partition. There are 4 logical partitions on that. They are /boot , / , /home , swap. I intend to make 2 more primary partitions on the remaining 30 gig and make them / and /home for the new distro.
   Can I use the logical swap partition on my extended partition for the new OS?  Same question for the /boot partition, and do I want to use the /boot partition?
  I am rather sure I can install on my unused space just not sure if I can use the swap and if I want to use the /boot partition. Grub still gives me a scare so that is really my only worry.
  Thanks in advance,
        Joe

---

### Post by shifty_powers on 2009-06-16
really would not recommend using the same boot partition, as the two distros may use different kernels, which would cause issues.

i think you would be able to use the swap mind...

---

### Post by LewRockwell on 2009-06-16
use separate partitions for each distro

if you have problems with grub you can burn one of these:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

also, while you're at it, burn on of these to play around with:

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

---

### Post by Miljet on 2009-06-16
When you install the new system it should find, and use, an existing swap partition, no matter where on the drive it is located.

Whenever I install a different distro, I look for an option under an advanced tab to NOT install a boot manager. It is far easier to edit your existing menu.lst file to add the new install.

---

### Post by JoePublic9 on 2009-06-16
Thanks all.
  I will let it use the swap file I have and I will not install grub.
I will have to learn to edit grub to add a distro. Should be fun.
  Thanks again.  
       Joe

---

