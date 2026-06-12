---
title: "Installing apps in a specified location"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by tushar_t on 2009-08-08
Hi,

I've installed Ubuntu on my Asus Eee PC on the 4GB SSD internal drive. I'd like to install additional packages on a SDHC card which I keep inside the SD-slot of the netbook. Is that possible?

Thanks.

---

### Post by Nepherte on 2009-08-08
Possible? Yes. Easy? No. You would have to mount the sd card to a specific mounting point and compile the software yourself with a specific prefix. That or reinstall your system and use LVM to merge several disks into one partition.

If you don't have a separate /home partition you could also use that sd card as your home, leaving you with more space for everything else.

I'd personally try to remove some unused packages but I understand that 4 gig is not much.

---

### Post by tushar_t on 2009-08-08
Cheers.

For now I just need to install Eclipse and I have a shade over 1 GB left so I should be fine. But I wanted to know for future reference. I think removing packages is a good idea, and I'll start with that. There are quite a few programs in there that I won't use.

> That or reinstall your system and use LVM to merge several disks into one partition.

I like this idea. How difficult is it to do?

A quick google search brought me here: [http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem](http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem)

Would that be the correct way to go about it?

Thanks again.

---

