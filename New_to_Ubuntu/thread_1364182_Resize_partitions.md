---
title: "Resize partitions"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-25
Hello again!

I just got a new HDD for christmas and I'm trying to install it. 

So here's the thing:
I had this Debian server that I put the hard drive into, and then used clonezilla to clone the hard drive over. Now I need to resize the partitions... since my hard drive is bigger.

So I load up Gparted on the ubuntu live CD and I look at my partitions. (see screenshot) and then get ready to resize my boot/swap/etc. partitions. The problem is that I can't simply increase the size of my linux partition, since the logical/swap partition is in the way. Mainly I just don't want to screw around with my partitions and mess something up horribly... so I decided to ask for help :P

Any ideas?
What should I do?

---

### Post by darkeye123 on 2009-12-25
Whoops... forgot to attach the screenshot. [facepalm]

---

### Post by tom.swartz07 on 2009-12-25
Ive done this about 10 times. Nice and easy.

You should do each of these steps one at a time, and make sure that everything is backed up first. (hopefully you didnt trash the old drive yet, since you just copied everything)


Looking at your drive, it seems that your swap space is located in the extended partition, so you *shouldnt* have to change its size, unless you also upgraded your RAM. (Swap should be about the same size as ram, so that you could hibernate, etc)

First, just shift the entire extended partition sda2 to the end of the drive. You could just click and drag it to the end, rather than move the ends.

Next, select the partition with your Linux distro on it, sda1, and extend it all the way to the right.

It shouldnt take too long, because youre just extending it into blank drive space. Normally, if you have data already on the drive it takes a while.

After that, open your terminal and run 
```
update-grub
```
just to make sure that your bootloader is complete, and then youre all set!

Congrats on your massive upgrade!

---

### Post by warfacegod on 2009-12-25
> (Swap should be about the same size as ram, so that you could hibernate, etc)

Not necessarily, having swap depends entirely on how you intend to use the computer and how much RAM you have. If you have lots of RAM (2GB or more) your swap partition may never be used (as far as I've noticed, mine hasn't) unless you hibernate. Theoretically, unless you use hibernation, you may never need swap. The only reason I have one is because I am too lazy to tell the partitioner to not create one when I do an install.

---

### Post by darkeye123 on 2009-12-25
Thanks a lot Tom.swartz!
Worked like a charm :P

---

### Post by tom.swartz07 on 2009-12-25
> **darkeye123 said:**
> Thanks a lot Tom.swartz!
Worked like a charm :P

Glad to help!
Please mark the thread as [Solved] from the thread tools, so that others could be helped by your post!

Merry Christmas, and enjoy all that new space!

---

