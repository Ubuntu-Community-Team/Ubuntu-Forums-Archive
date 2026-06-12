---
title: "how much for swap?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by natman on 2009-04-24
Hi,
I am about to install 904 and will be doing the manual partition option, how much should i give for swap? My laptop has 3gb of ram, but i remember on my old laptop( 2gb ram ) i very rarely actually used more than 1.5gb of ram. So would i get away with only 1.5gb for swap - will suspend/resume still work or do i need to give it the full 3gb?
Thanks:
Patrick

---

### Post by tom56 on 2009-04-24
Suspend/resume will work but hibernate won't. A good rule of thumb is 1.5x your physical memory.

---

### Post by konqueror7 on 2009-04-24
i have a 2gb ram, and i allocated only 1gb of swap...still able to use hibernate...

---

### Post by Sir Jasper on 2009-04-24
Hi,

If you are short of space, you could try the minimum as you can use Gparted to change the size of your swap partition. Alternatively you could make a swap file.

I only have 640 MB and I usually use "sudo swapoff /dev/sdb5" so that my sdb5 swap partition cannot be used as it doesn't seem to slow me down or make any obvious difference.

The other important factor is power usage, where sometimes the swap partition or file has to be at least as big as RAM.

My regards

---

### Post by tom56 on 2009-04-24
> **konqueror7 said:**
> i have a 2gb ram, and i allocated only 1gb of swap...still able to use hibernate...

Sometimes it will work. But if you are using all the RAM when you choose to hibernate (which is likely, since you are only likely to want to hibernate when you have lots of programs open) it will fail, because there is not enough space on the swap partition to save the data in the RAM there (which is what happens when you hibernate).

---

