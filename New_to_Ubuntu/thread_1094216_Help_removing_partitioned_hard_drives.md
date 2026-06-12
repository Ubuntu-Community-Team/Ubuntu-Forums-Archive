---
title: "Help removing partitioned hard drives"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by IncessantLearner on 2009-03-12
Hello everyone! I am glad to be posting here as this is my first post.

So last April a friend told me about Ubuntu and I figured I'd try it out. I set it up off a burned disk, partitioned my hard drive and I got to try it out for the last 2 weeks of school. When I moved out, I lost the password that I had written down. Additionally, I forgot the password and username because I left the computer at home for 4 months as I had no internet where I was living.

I was wondering, since I updated my computer to Intrepid Ibex and have been using it since, I was wondering if I could either: 

A) Some how access the Hardy Heron partitioned drives to remove them and free up space on my hard drive.

B) Remove the partition from my hard drive without trying to access Hardy Heron.

I am sure there may be other ways to do this and I am open to suggestions. 

I have limited exposure to Linux and partitioning hard drives but I am excited about the platform and just downloaded the Ubuntu Pocketbook to read!

---

### Post by Therion on 2009-03-12
Your best bet would be to use a Parted Magic LiveCD.

[http://wiki.partedmagic.com/index.php/Downloads](http://wiki.partedmagic.com/index.php/Downloads)

Boot to the CD and it will allow you to move, resize and remove partitions using a graphical interface.  You'll want to remove the Hardy Heron partition of course, and then expand the Intrepid partition to include it.  Everyone should have one of these CD's handy in my opinion!

---

### Post by Elfy on 2009-03-12
Yes you can - assuming that the hardy partition is not mounted you could use a partition editor from within intrepid, it just needs to be installed.

You could then have it as a seperate data partition. If you wnated to add it to the intrepid partition, you would need to boot the livecd to do so, or get a partition editor such as partedmagic.

If you are at all unsure which partition is which then post the results of

```
sudo fdisk -l
df -h
```

It is a simple enough procedure in itslef - but make sure you have backups of any critical data before you start just in case of problems.

As an aside you could have retrieved the username and reset it's password when you lost the hardy stuff ;)

---

