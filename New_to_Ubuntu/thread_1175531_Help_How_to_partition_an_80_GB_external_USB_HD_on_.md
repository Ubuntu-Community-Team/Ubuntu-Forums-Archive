---
title: "Help How to partition an 80 GB external USB HD on which I'd like to install Jounty?"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by ke6rj on 2009-06-01
Can anyone please suggest how to partition during the install? On it are are 24 Gig of data and 50 are free. If I have to, I could live without the 24 Gig data. My question is, when I partition, how much for each and which one first, Do I first partition 
"/" (ext3) and allocate maybe 20 GB?
"/home" (ext3) 10 GB?
"/data" 20 GB?
"/boot" 2 GB (I have 2 GB Ram on my Dell Laptop)
I assume I do all this with the "Manual" option.
My hope is to be able to take the USB external HD to other machines and use Ubuntu without needing to install on the other machines.
Harry

---

### Post by mike555 on 2009-06-01
I would not have a separate /home partition, although many people recommend it I think it's better just to have a separate partition for backup of your home , and setup a backup app to do it automatically ..... that way your harddrive arm isn't bouncing around between your operating system partition and your /home partition ........ which can be a lot if you have your operating system on the first section of your harddrive and your home on an outside section of your harddrive ...... it would be kinda like "swap filing" , you know how that slows your computer down ....

---

### Post by Miljet on 2009-06-01
To Mike555:
That is a very valid point. I have never heard it put that way, but it makes sense to me. I like the idea of a data backup partition.

To ke6rj:
I don't see any need for a separate /boot partition. The only reason to have one would be if you constantly experiment with different distros and want to keep your GRUB from being overwritten. I suspect that you are confusing a /boot partition with a swap partition (which I don't see mentioned.) The swap partition size should be at least the size of your RAM.

---

### Post by Hospadar on 2009-06-01
There's a good writeup on your options in the documentation:

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I personally enjoy having a separate home partition, it makes upgrades and re-installs very painless

---

### Post by ke6rj on 2009-06-07
Thank you for your help.

---

