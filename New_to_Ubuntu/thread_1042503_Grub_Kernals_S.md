---
title: "Grub Kernals :S"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by azz2811 on 2009-01-17
when i turn on my comp three kernals come up: 1 of them is sickboys kernal for Acer aspire ones.  one of them is the keral that first was on there when i installed ubuntu and then the other one just showed up after i updated the system.  The other 2 (not sickboys) they also have recovery kernals.  i was wondering how do i delete all of the kernal except for sickboys because that is the only one i want. thanks

---

### Post by Muffinabus on 2009-01-17
They are there for recovery purposes in case your current kernal goes bad.  You are best off just leaving them there.

---

### Post by seagullplayer77 on 2009-01-17
> **Muffinabus said:**
> They are there for recovery purposes in case your current kernal goes bad.  You are best off just leaving them there.

He's got a good point. Yeah, having a big list of kernels can be a pain, but it's certainly not bad for your computer. If the kernel you're currently using goes bad, then you have two other kernels you can use to get at your data with. It's a good safety blanket, and since it doesn't hurt, I'd just leave them there.

If you *really* wanted to get rid of the other kernels, I suppose you could edit /boot/grub/menu.lst and just comment out the sections for the kernels you don't want. I'm not entirely sure that would work, though, and I would recommend getting a second opinion before you try it.

---

### Post by cdtech on 2009-01-17
Removing kernel images is best done through the "Synaptic Package Manager". You can edit your menu.lst file to only allow current images:
> howmany=all
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options## e.g. howmany=all
##      howmany=7
# howmany=all
This controls how many kernels can be listed in the kernels list. Each time a kernel is updated it is added at the top of the list and the old kernel remains in the list, but is moved down.
If you don't like having a big long kernels list and having to hash out or delete kernels, then unhash 'howmany=all', and replace 'all' with a number of your choosing.
Taken from here:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ajgreeny on 2009-01-17
Yes, keep two kernels which you know work OK, but remove all the older ones with synaptic.  The disk space on these netbooks is quite small, so it is a pain if too many kernels take valuable space.

---

