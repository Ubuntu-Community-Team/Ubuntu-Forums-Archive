---
title: "Resize swap file partition."
date: 2010-11-19
forum: New to Ubuntu
---

### Post by ben.jester on 2010-11-19
Excuse my ignorance but how do I re-size the swap file partition after doing a memory upgrade ?? (Ubuntu 10.04 LTS) 

I'm sure this will have been asked many times before but I haven't managed to find the answer yet. Any help gratefully received.

Regards... 

Bennie The Ball

---

### Post by coffeecat on 2010-11-19
You may not really need to resize your swap, depending on whether you use hibernate. If you do need to resize the swap partition, this can be done with Gparted, most often best from the live CD depending on your partition layout.

Please post this information.

How much RAM do you have now? Now open a terminal and post the output of:

```
sudo fdisk -lu
```With that someone can advise you how to resize your swap partition, if that is feasible, and whether or not it is worth doing.

---

### Post by sikander3786 on 2010-11-19
How much swap and RAM you've currently?

Infact I didn't need Swap on my 3GB RAM PC unless you are hibernating.

To add swap, see this.

[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by ratcheer on 2010-11-19
> **ben.jester said:**
> Excuse my ignorance but how do I re-size the swap file partition after doing a memory upgrade ?? (Ubuntu 10.04 LTS) 

I'm sure this will have been asked many times before but I haven't managed to find the answer yet. Any help gratefully received.

Regards... 

Bennie The Ball

I doubt that it can be done if there is no unallocated free space contiguous with the existing swap partition.  You could install and load gparted to delete the current swap partition and add a new one that is the size you want (again, assuming you still have unallocated space on the disk). But then, the original swap partition's space would be pretty much wasted.

Another alternative would be to add a second swap partition, with the second one large enough that the two swaps total to what you want. Ubuntu will use multiple swap partitions, though this is usually done when you have multiple disk drives.

Others will probably have more ideas.

Tim

---

### Post by ben.jester on 2010-11-19
just upgraded to 2G. Will be doubling up again at a later date.

---

### Post by ben.jester on 2010-11-19
Current swap partition is only 512mb which was the available ram in the machine when it was new. If the machine will run with a 2gb upgrade without the need to change the size of the swap partition that's fine, but the original install disc said that the swap partition needs to be the same size as the installed ram.

---

### Post by sikander3786 on 2010-11-19
> **ben.jester said:**
> Current swap partition is only 512mb which was the available ram in the machine when it was new. If the machine will run with a 2gb upgrade without the need to change the size of the swap partition that's fine, but the original install disc said that the swap partition needs to be the same size as the installed ram.
Unless you are hibernating, and not running any memory hungry applications, 2GB RAM is enough for Ubuntu. And then you are also going to double that in the next few days?

For the moment, you can keep an eye on **free** frequently from Terminal and see if you need extra Swap.

```
free
```

---

### Post by coffeecat on 2010-11-19
> **ben.jester said:**
> the original install disc said that the swap partition needs to be the same size as the installed ram.

It needs to be the same size **if** you use hibernate. Otherwise you may not need so much swap. However, we cannot advise you whether it is possible to resize your swap partition unless you post the output I suggested earlier.

---

