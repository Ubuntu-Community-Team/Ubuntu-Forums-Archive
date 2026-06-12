---
title: "My computer cant hibernate"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by ja660k on 2009-03-08
Hi, 
When im at university i find myself using my laptop at different times of the day for short periods, and instead of turning it off/on each time im wanting to know if i can put it on hibernate, and i tried just before

and i got different exceptions and stuff and i had to turn it off and back on.

ive heard that ubuntu, well all linux distros struggle with this..? is that true. and what can i do?

---

### Post by Dadsgé on 2009-03-08
maybe your swap-area isn't big enough?

---

### Post by ja660k on 2009-03-08
how do i find out what is big enough. and fix said problem

---

### Post by Dadsgé on 2009-03-08
well, that's the part i don't now to solve the problem...
i set it up with 100Mb and it works fine, although i don't use it often.

just googled it
check: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) ;)

---

### Post by Miljet on 2009-03-08
In order for your machine to hibernate, everything in memory must first be written to disk - in the swap partition. Therefore the swap partition must be at least as large as the installed memory. It is a good idea to include a little extra also. In other words, if you have 1gb memory, set up swap partition with one and a half gb.

If needed, you can adjust swap partition using gparted from the liveCD. You will probably have to shrink some other partition to make space available for the swap.

Be sure to back up important information before changing partition sizes.

---

### Post by ja660k on 2009-03-08
uhh... my swap space is big...

see the screenshot i just took
[http://imagebin.org/40522](http://imagebin.org/40522)

i have 5.6gb of swap?

---

### Post by TheGoblin on 2009-03-28
OK, I just finished 12 hours of figuring out why my laptop wouldn't hibernate after changing to using a new second, larger swap partition, so the following info might be useful to you:

[LIST=1]
[*]Under Hardy, if you are using a swap partition whose partition number is smaller than another, second (unused) swap partition on your disk, swsusp will refuse to write the memory image to disk with an error similar to 'cannot find swap device, try "swapon -a"'. The solution to this is to use GParted to change the partition type of the unused swap partition to something other than linux-swap, like ext2 (use the "format" menu entry under "Partition"). Probably just deleting the unused swap partition would work also, but I didn't check that.

[*]After solving the first problem, the laptop would write the memory image but not restore from it. The solution to this was found at [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637/comments/23]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637/comments/23"). You can also use the "vol_id" command to find the proper UUID to put in /etc/initramfs-tools/conf.d/resume .

[/LIST]

---

### Post by flostre on 2009-04-01
If the content of the memory goes into the swap partition for hibernation, where does the stuff go that is in the swap partition?

---

