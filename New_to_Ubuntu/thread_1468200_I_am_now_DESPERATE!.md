---
title: "I am now DESPERATE!"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by khjui on 2010-05-01
Okay, so: 
When I installed Ubuntu I made the foolish mistake of only allowing it to have 13gb, so after a few days I ran out of space.

I have cleared up 29gb of space, I have gone to gParted, and it says that it can't read my 13gb Partition, and I therefore can't resize it.
I have spent days and days trying to find a way to change this, trolled the net to try and fine a solution and found absolutely NOTHING.

Then I decided to delete my 13gb Partition, which didn't seem to change a thing?
I tried making a new partition from the 29gb unallocated, but it didn't work.
So I have re-created the 13gb Partition, and now only have 23mb of space free.

This is what gParted looks like:

[[img]http://images.roflcopter.net/thumb/4112.jpeg[/img]](http://images.roflcopter.net/view/4112)

Please Help! I am DESPERATE!

-Tom

---

### Post by sidewalkcynic on 2010-05-01
If you are using GParted while using the operating system on the partition you want to adjust, it won't work - it only works for adjusting other partitions.

What you need to do is load the live CD, or live USB, and use the GParted application on that to adjust partitions that otherwise would be in use. And be advised: It has been my experience that adjusting Ubuntu OS partitions corrupts the OS, so the OS has to be reinstalled on the adjusted partition. So, it is easier to delete the partition and then just resize during installing.

Get it?

Just reinstall, delete and make a new larger partition then.

---

### Post by khjui on 2010-05-01
WHen I try to run the Live CD...my computer freezes up :S

---

### Post by themusicalduck on 2010-05-01
One thing I noticed is that /dev/sda3 is mounted at /host. Did you install this with Wubi? Or are you trying to do a dedicated install onto it's own partition?

I'm still not clear on what you actually want to do though. You want to make a new partition of what size? To install Ubuntu on right? Bear in mind that you should format the partition as ext4, not Fat32 to install Ubuntu onto it. Also you must re-partition from a liveCD (boot up with the Ubuntu CD and select to run it without changing your computer). This is because you can't resize or format a partition if any partition on the hard drive is mounted.

There is some information on partitioning in the Ubuntu manual - [http://ubuntu-manual.org/](http://ubuntu-manual.org/) Although it's specific to 10.04

 
Also there might be more specific information here - [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Paqman on 2010-05-01
> **themusicalduck said:**
> One thing I noticed is that /dev/sda3 is mounted at /host. Did you install this with Wubi? 

I'd say so. /host is the hallmark of a Wubi install.

khjui, you can't resize your partitions with Gparted if they're not actual disk partitions. Wubi creates a virtual partition that's actually just a big file on the Windows partition. To resize it you need to use [LVPM]("http://lubi.sourceforge.net/lvpm.html").

---

### Post by khjui on 2010-05-01
> **themusicalduck said:**
> One thing I noticed is that /dev/sda3 is mounted at /host. Did you install this with Wubi? Or are you trying to do a dedicated install onto it's own partition?

I'm still not clear on what you actually want to do though. You want to make a new partition of what size? To install Ubuntu on right? Bear in mind that you should format the partition as ext4, not Fat32 to install Ubuntu onto it. Also you must re-partition from a liveCD (boot up with the Ubuntu CD and select to run it without changing your computer). This is because you can't resize or format a partition if any partition on the hard drive is mounted.

There is some information on partitioning in the Ubuntu manual - [http://ubuntu-manual.org/](http://ubuntu-manual.org/) Although it's specific to 10.04

 
Also there might be more specific information here - [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Yes, I used Wubi.
So ext4...

---

### Post by carl4926 on 2010-05-01
It's also a right mess. How on earth did you end up with that.

Boot up Parted Magic
it's a life saver

---

### Post by khjui on 2010-05-01
> **carl4926 said:**
> It's also a right mess. How on earth did you end up with that.

Boot up Parted Magic
it's a life saver

Whats Parted Magic?

---

### Post by _0R10N on 2010-05-01
wow, this thread is getting as messy as that disk! lol. khjui, why don't you start from scratch here. We need to know four things:
1- What you want.
2- What you got.
3- How did you ended up with that. (wubi install)
4- Scenario, existent disk partitions, original disk partitions, host OS (in case of wubi,

I'm proposing this because I can't get to what you're trying to do though, and I consider that other people trying to help you, will fall under that problem, also.

---

### Post by khjui on 2010-05-01
> **_0R10N said:**
> wow, this thread is getting as messy as that disk! lol. khjui, why don't you start from scratch here. We need to know four things:
1- What you want.
2- What you got.
3- How did you ended up with that. (wubi install)
4- Scenario, existent disk partitions, original disk partitions, host OS (in case of wubi,

I'm proposing this because I can't get to what you're trying to do though, and I consider that other people trying to help you, will fall under that problem, also.

I need to increase the size of my main partition (the one used for /home)

---

### Post by carl4926 on 2010-05-01
[http://lmgtfy.com/?q=parted+magic](http://lmgtfy.com/?q=parted+magic)

Anyone worth their salt would wipe that disk and start again.

---

### Post by _0R10N on 2010-05-01
> **carl4926 said:**
> [http://lmgtfy.com/?q=parted+magic](http://lmgtfy.com/?q=parted+magic)

Anyone worth their salt would wipe that disk and start again.

Yeah, it might be the fastest and reliable thing to do.

---

### Post by Paqman on 2010-05-02
> **carl4926 said:**
> [http://lmgtfy.com/?q=parted+magic](http://lmgtfy.com/?q=parted+magic)

Anyone worth their salt would wipe that disk and start again.

Guys, this is a Wubi install. There are no partitions to modify. Please stop making confusing (and in the case above, somewhat facetious) posts.

He needs to expand his loopmounted virtual partition. For that he'll need LVPM, as explained in the [Wubi guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?").

---

