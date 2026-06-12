---
title: "Removing Swap Partition"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Djalmahal on 2009-04-05
Hi,

my hard drive is running out of space on my old laptop. I have a 5 GB Swap partition but i have 2gb RAM, so my RAM is never fully used. Can I free up to 5 GB swap to use?
I ran sudo gparted but i don't seem to be able to remove that partion. How can I do that?

Thanks
Andreas

---

### Post by ninjapirate89 on 2009-04-05
I'm not 100% sure but I don't think you can expand a partition that you are currently using. You'll probably have to use a live cd to do it.

---

### Post by glotz on 2009-04-05
[QUOTE=ninjapirate89]You'll probably have to use a live cd to do it.[/QUOTE]That's right. [Here's](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779) the latest gparted live cd.

---

### Post by asmoore82 on 2009-04-05
you may free up some space with
```
sudo apt-get autoremove
sudo apt-get clean
```

and by removing old kernels in synaptic if you don't need them.

---

### Post by Hospadar on 2009-04-06
5 Gb! Holy cowpies batman!

You shouldn't need such a large swap really.  Even on a full load I think ubunutu for most people would have trouble filling up 2G unless you run some really [memory] leaky programs.  So when you have 2Gb of ram, You probably would be safe with a swap more on the order of 512Mb

You can just resize your partitions to shrink down your swap and grow your main partitions into the free space.

You will need to boot off a livecd, Alt-F2->"gksu gparted"
Before you can change/delete/resize your swap, you'll need to deactivate it (even the livecd will detect and start using a swap partition)
I think in gparted you can just right click the swap and choose "swapon/swapoff", alternatively you can run "sudo swapoff" in a terminal before you start up gparted.
After that you can do all the normal gparted delightfullness to handle your partitions

---

### Post by ninjapirate89 on 2009-04-06
> **Hospadar said:**
> 
I think in gparted you can just right click the swap and choose "swapon/swapoff"

Yes you can do this.

---

### Post by asmoore82 on 2009-04-06
[COLOR="Red"][SIZE="3"]**!!! Warning !!!**[/SIZE][/COLOR]

To little or no swap space on laptops breaks Hibernation functionality.
But, personally, that wouldn't bother me at all, I much prefer "Sleep/Stand-by"

---

### Post by JoshuaRL on 2009-04-06
I'd say drop that thing down to about 1GB.  [Here's the site for Parted Magic.](http://partedmagic.com/)  I'd suggest that, it's a live CD that has gparted on it.  Really easy.

---

### Post by trinidadflores on 2009-04-06
> **Djalmahal said:**
> Hi,

my hard drive is running out of space on my old laptop. I have a 5 GB Swap partition but i have 2gb RAM, so my RAM is never fully used. Can I free up to 5 GB swap to use?
I ran sudo gparted but i don't seem to be able to remove that partion. How can I do that?

Thanks
Andreas

Let me guess you chose to allow ubuntu to take over the whole HD when you installed it?  I did and it allowed 9.42 gb for my swap.  And I have 4 gb of ram using the 64 bit version!

---

