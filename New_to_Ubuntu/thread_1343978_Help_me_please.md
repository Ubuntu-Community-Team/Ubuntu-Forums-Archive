---
title: "Help me please"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by KAMPARman on 2009-12-02
Dear sir,
I like to install ubuntu 9.10 alone with out any other operating system. But i don't know how. Can you help me? I have 80 gb of hard disk, 2 gb of ram and i using pentium 4 3.0. Where should i install ubuntu? How many partition should be create? How about the size of partition? Please help me. Thank you.

---

### Post by jbrown96 on 2009-12-02
You need to burn the Ubuntu image to a disk, or install it on a flash drive. [Here]("https://help.ubuntu.com/community/BurningIsoHowto") are some good instructions.


Partitions:
I don't recommend creating a swap partition because it's hardly ever needed. 
Create two partitions.
#1  size: 12GB, file system: ext4, mount point: /
#2 size: rest of disk, file system: ext4, mount point: /home

---

### Post by lisati on 2009-12-02
I would recommend a swap partition, because it can help system performance, particularly if you're going to do some resource-hungry stuff e.g. video editing.

First of all, get hold of an Ubuntu CD: [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
If you choose do download and burn a CD for yourself, some good information can be found here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Since you're looking to have only Ubuntu on your system, you'll need to boot from the CD. If you need help doing this, feel free to ask. When the CD starts, your best bet is to use the option to try Ubuntu without installing it first. This will run a bit slower than a full install, but can help you see if it works on your system.

---

### Post by QIII on 2009-12-02
Swap is necessary for hibernation, otherwise known as "suspend to disk".

For safety, I recommend 1.1x to 1.25x RAM.  Others say 2x.

---

### Post by oOarthurOo on 2009-12-02
Don't worry about partitions and swaps and such. Just put the cd in the drive and answer the few questions it asks you. When it asks you how you want to partition the disks, just tell it to uses the whole drive and it will automatically make some sensible choices for you.

---

### Post by Dougie187 on 2009-12-02
> **QIII said:**
> Swap is necessary for hibernation, otherwise known as "suspend to disk".

For safety, I recommend 1.1x to 1.25x RAM.  Others say 2x.

I agree with this recommendation. Anymore will be a waste of your precious disk space. Especially since you only have 80gigs.

So, 3 partitions,

1 - Swap - Format=Swap - Size=~2GB
2 - Root - Format=Ext4 - Size=~12GB-15GB - MountPoint=/
3 - Home - Format=Ext4 - Size=Remaining - MountPoint=/home

---

### Post by QIII on 2009-12-02
> **oOarthurOo said:**
> Don't worry about partitions and swaps and such. Just put the cd in the drive and answer the few questions it asks you. When it asks you how you want to partition the disks, just tell it to uses the whole drive and it will automatically make some sensible choices for you.

Depends on what you think is sensible.

I think a separate /home partition is sensible, which you do not get if you just follow the path blindly.

---

### Post by camaron1 on 2009-12-02
> **oOarthurOo said:**
> Don't worry about partitions and swaps and such. Just put the cd in the drive and answer the few questions it asks you. When it asks you how you want to partition the disks, just tell it to uses the whole drive and it will automatically make some sensible choices for you.
Although this is true to have a separate home partition is far better. If you make the effort to do this you won't regret it as you might eventually if you don't. It makes me wonder why a separate root/home partition isn't the fact default installation. A swap partition is optional.

Good luck by the way

---

### Post by jbrown96 on 2009-12-02
I have a laptop with 2GB of memory. I've used linux for 3 years, and I have never, ever touched my swap partition. Never even close. I stopped using one about a year ago, and I haven't had any problems. Ubuntu simply doesn't use 2GB of memory. Even when doing something particularly memory intensive like Virtualization, I have used swap. 

It's really just a waste of disk space. The only situation where it makes sense if hibernate, but suspend is far superior anyways.

---

### Post by camaron1 on 2009-12-02
> I have a laptop with 2GB of memory. I've used linux for 3 years, and I have never, ever touched my swap partition. Never even close

That's not my experience though, I've got 2.8 gigas of memory and swap is used regularly when i'm approaching  1 giga of use. I have always wondered why this was the case.

---

### Post by oOarthurOo on 2009-12-02
If KAMPARman feels comfortable creating partitions then creating a separate /home partition is a good idea. In which case I'd recommend 8GB formatted to ext4 mounted to /, 2.5GB mounted to /swap, and the rest formatted to ext4 mounted to /home.

If any of the above sounds confusing or intimidating to you just let Ubuntu use the disk and rest easy knowing you're doing things the same as a great many other Ubuntu users.

---

### Post by jbrown96 on 2009-12-02
> **camaron1 said:**
> That's not my experience though, I've got 2.8 gigas of memory and swap is used regularly when i'm approaching  1 giga of use. I have always wondered why this was the case.

That is certainly not normal.

---

### Post by ssulaco on 2009-12-02
> **KAMPARman said:**
> Dear sir,
I like to install ubuntu 9.10 alone with out any other operating system. But i don't know how. Can you help me?
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

