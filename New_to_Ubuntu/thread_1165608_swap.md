---
title: "swap"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Ceiber Boy on 2009-05-20
swap?! i have 500Mb of memory, 150Mb used and 0% swap. dose swap only come into use when the memory full or anything else? i really don't understand how this works!

---

### Post by Zzl1xndd on 2009-05-20
This might help

[http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)

---

### Post by damis648 on 2009-05-20
Swap space is for use when physical memory is low. If your physical memory (that 500mb you have) gets filled up, swap is used. Swap is also used for hibernation, so I recommend to always have a swap partition greater than or equal to the amount of RAM you have.

---

### Post by Ceiber Boy on 2009-05-20
> **damis648 said:**
> Swap space is for use when physical memory is low. If your physical memory (that 500mb you have) gets filled up, swap is used. Swap is also used for hibernation, so I recommend to always have a swap partition greater than or equal to the amount of RAM you have.

from the terminal i tried to increase the amount of swap, but it will not allow me to enter a figure greater than 100, making it impossible to have it greater than my memory value of 500!

---

### Post by Miljet on 2009-05-20
The size of swap is determined by the size of the swap partition that was created during installation. The only way you can change it is to change the size of your partitions.

---

### Post by Ceiber Boy on 2009-05-20
> **Miljet said:**
> The size of swap is determined by the size of the swap partition that was created during installation. The only way you can change it is to change the size of your partitions.

is this something that was calculated automatically during installation? and can i change it manually using the terminal?

---

### Post by Zzl1xndd on 2009-05-20
> **Ceiber Boy said:**
> is this something that was calculated automatically during installation? and can i change it manually using the terminal?

Its normally automatic, in most cases it gives you more then enough . How much does it say you have?

---

### Post by Ceiber Boy on 2009-05-20
> **tweakedenigma said:**
> Its normally automatic, in most cases it gives you more then enough . How much does it say you have?
 
default 60, but i increased it to 100

---

### Post by jimingkui on 2009-05-20
> **damis648 said:**
> Swap space is for use when physical memory is low. If your physical memory (that 500mb you have) gets filled up, swap is used. Swap is also used for hibernation, so I recommend to always have a swap partition greater than or equal to the amount of RAM you have.

Thanks,I've on idea of swap as far as your reply

---

### Post by Zzl1xndd on 2009-05-20
> **Ceiber Boy said:**
> default 60, but i increased it to 100

That sounds like you changed the Swappiness value. Your actual swap partition is likely larger then you think. Just go to System > Administration > system monitor, From here check the resource tab it should tell you how much swap you have.

---

### Post by XCan on 2009-05-21
If you don't want to resize your swap partition in case you want more swap, there's a quick and dirty way to add more swap by creating a swap file. A pretty good guide can be found here [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by camper365 on 2009-05-22
I think the way it works when you do it automatically is it doubles the amount of RAM you have, I may be wrong though. I do all the partitioning manually when I install.

---

