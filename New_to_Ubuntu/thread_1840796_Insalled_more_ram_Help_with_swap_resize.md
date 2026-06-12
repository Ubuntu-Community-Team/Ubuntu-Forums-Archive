---
title: "Insalled more ram Help with swap resize"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by SushiAddiction on 2011-09-08
I had 4GB of memory and 9GB swap.
I installed another 8GB of memory :P so now I have 12GB memory

I have 'put computer to sleep' after 1h in power management.
(does sleep mean suspend?) 

The memory is written to the swap file when you hibernate, right? So I'll need at least a 12GB swap for hibernation.

Should I use gparted on a live cd to increase the swap partition or is there another way.

---

### Post by Enigmapond on 2011-09-08
In truth, with that much RAM, you don't even need swap. Swap is highly overrated.

---

### Post by snip3r8 on 2011-09-08
What on earth do you use that much memory for?

---

### Post by SushiAddiction on 2011-09-08
> **snip3r8 said:**
> What on earth do you use that much memory for?
That's not an answer :(
So ubuntu never uses the swap file instead of ram. :P and to make use of  /dev/shm/

---

### Post by Johnb0y on 2011-09-08
> **SushiAddiction said:**
> You don't need to tell me that I've read that answer soooo many times in other posts

All I need to know is that I won't stuff anything by resizing the partition with a live cd using gparted... or if there is a better way to do it.

Hiren CD has lots of tools you can use for resize/partition drives....

---

### Post by btindie on 2011-09-08
You don't need swap to be able to suspend your computer. When you suspend it it simply gets put into a low power state, the RAM still receives power and thus whatever's there stays there.

It's only when you want to hibernate your computer that you need swap, as that's when it then writes the contents of RAM to the swap. It may be cleaver enough to only write the used portion of RAM to swap to save time, I don't know? I think there's an alternative to using a swap partition and that is a swap file so you can just allocate a large file on your root and have it use that instead.

[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by samstreet101 on 2011-09-08
I've always found gparted to be more than adequate at resizing partitions. If you have windows installed on your computer it usually does a chkdsk (check disk) if you resize a partition that it can see. Other than that I've had no problems.

---

### Post by SushiAddiction on 2011-09-08
> **btindie said:**
> You don't need swap to be able to suspend your computer. When you suspend it it simply gets put into a low power state, the RAM still receives power and thus whatever's there stays there.

It's only when you want to hibernate your computer that you need swap, as that's when it then writes the contents of RAM to the swap. It may be cleaver enough to only write the used portion of RAM to swap to save time, I don't know? I think there's an alternative to using a swap partition and that is a swap file so you can just allocate a large file on your root and have it use that instead.

[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Yeh hibernate uses swap. I do use hibernate sometimes; Moving computer, Thunder Storms, Other really important times too.
Swap Partition is contiguous and swap file is not. Call me obsessive....... 

EDIT> " It may be cleaver enough to only write the used portion of RAM to swap to save time" tested -->YES that is what it does

> **samstreet101 said:**
> I've always found gparted to be more than adequate at resizing partitions. If you have windows installed on your computer it usually does a chkdsk (check disk) if you resize a partition that it can see. Other than that I've had no problems.

GParted is good. I just thought I might need to change something along with the resize but I guess not.
I just found this
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If I can't resize, this is going to be difficult.
I can see myself using a whole saturday for this ](*,) All this just to watch and encode pawn on several monitors at once :D ... just joking

---

### Post by mcduck on 2011-09-08
Hibernating doesn't actually require as much swap as you have RAM, but instead as much as you have used RAM at the moment (excluding any buffers and cache). So unless you really are using more than the 9GB you now have you shouldn't have any problems.

Anyway, increasing swap is quite simple in the end, just increase the size of the swap partition like you would any other normal partition, use the mkswap command to format the partition as swap and finally make sure that the UUID for the swap partition is correct in /etc/fstab. 

It is also possible to use a swap file instead of a partition, or even use both at the same time for an easier & more flexible way to adjust the amount of swap you have.

---

