---
title: "What is the difference in ext3 and ext4?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by tekkieguy on 2009-03-29
I had ubuntu 9.04 and than i   decided to give Kubuntu a try, so i installed it by a USB drive. I noticed that there was ext4, and i got a little excited because i have heard news that that would be faster. So i used ext4, and all seems good. But what exactly is the difference between those two

---

### Post by Lisa Y on 2009-03-29
The main benefits that ext4 has over ext3 are:

    * faster timestamping
    * faster file system checking
    * journaling checksums
    * extents (basically automatic space allocation to avoid fragmentation)

---

### Post by sdennie on 2009-03-29
And the downsides, as they currently stand are:

1) Vastly reduced reliability in the event of a crash (particularly pertinent when installing an alpha/beta OS where you expect crashes to happen).

2) Journal commit latencies under perfectly reasonable disk loads reaching the point of unusable.  An example of this would be downloading various (legal) video torrents while trying to also watch one.  The journal commit will often cause your video to skip.  Especially the longer you make it.

As I just said in another thread, as kernel development continues, the ext4 filesystem becomes less and less attractive.  Use ext3 for now.  You probably wouldn't notice the benefits between ext3 and ext4 in most cases so, for the moment, it's best to stick with ext3.

---

### Post by steve101101 on 2009-04-14
> **sdennie said:**
> And the downsides, as they currently stand are:

1) Vastly reduced reliability in the event of a crash (particularly pertinent when installing an alpha/beta OS where you expect crashes to happen).

2) Journal commit latencies under perfectly reasonable disk loads reaching the point of unusable.  An example of this would be downloading various (legal) video torrents while trying to also watch one.  The journal commit will often cause your video to skip.  Especially the longer you make it.

As I just said in another thread, as kernel development continues, the ext4 filesystem becomes less and less attractive.  Use ext3 for now.  You probably wouldn't notice the benefits between ext3 and ext4 in most cases so, for the moment, it's best to stick with ext3.

thanks for this very informative.

---

### Post by hesjnet on 2009-04-14
> **sdennie said:**
> 
As I just said in another thread, as kernel development continues, **the _ext4_ filesystem becomes less and less attractive.**  Use ext3 for now.  You probably wouldn't notice the benefits between ext3 and ext4 in most cases so, for the moment, it's best to stick with ext3.

Is this really what you meant?

---

### Post by Xispa on 2009-04-14
Ext4 FileSystem explained in plain english:
[http://hehe2.net/linux-general/ext4-filesystem-explained-in-plain-english/]("http://hehe2.net/linux-general/ext4-filesystem-explained-in-plain-english/")

---

### Post by steve101101 on 2009-04-14
i think he meant the other way. ext4 will eventually get more stable.  :lolflag:

---

### Post by skymera on 2009-04-14
> **sdennie said:**
> And the downsides, as they currently stand are:

1) Vastly reduced reliability in the event of a crash (particularly pertinent when installing an alpha/beta OS where you expect crashes to happen).

2) Journal commit latencies under perfectly reasonable disk loads reaching the point of unusable.  An example of this would be downloading various (legal) video torrents while trying to also watch one.  The journal commit will often cause your video to skip.  Especially the longer you make it.

As I just said in another thread, as kernel development continues, the ext4 filesystem becomes less and less attractive.  Use ext3 for now.  You probably wouldn't notice the benefits between ext3 and ext4 in most cases so, for the moment, it's best to stick with ext3.

I've found EXT4 to be much more reliable than EXT3 ever was. It is much faster and I haven't had any ill effects from writing to disk and watching videos. I have crashed Ubuntu and done about 10 hard reboots in 1 day. Did EXT4 complain? No, it done a check in a matter of seconds.

---

### Post by Paqman on 2009-04-14
> **skymera said:**
> I've found EXT4 to be much more reliable than EXT3 ever was. It is much faster and I haven't had any ill effects from writing to disk and watching videos. I have crashed Ubuntu and done about 10 hard reboots in 1 day. Did EXT4 complain? No, it done a check in a matter of seconds.

I'd go with that. There's a couple of things in Jaunty Beta that have been crashing with almost metronomic reliability (eg: compiz, npviewer, gnomad) and the filesystem has handled it just fine.

There's a reason why they've marked it stable. I'm confident that enough testing has been done.

---

### Post by leonardo_neo on 2009-04-14
> 
I've found EXT4 to be much more reliable than EXT3 ever was. It is much faster and I haven't had any ill effects from writing to disk and watching videos. I have crashed Ubuntu and done about 10 hard reboots in 1 day. Did EXT4 complain? No, it done a check in a matter of seconds.
__________________

+1. Agree with you.

---

### Post by sdennie on 2009-04-14
> **hesjnet said:**
> Is this really what you meant?

No, I meant, "Use ext3".

---

### Post by night_fox on 2009-04-15
> And the downsides, as they currently stand are:

1) Vastly reduced reliability in the event of a crash (particularly pertinent when installing an alpha/beta OS where you expect crashes to happen).

2) Journal commit latencies under perfectly reasonable disk loads reaching the point of unusable. An example of this would be downloading various (legal) video torrents while trying to also watch one. The journal commit will often cause your video to skip. Especially the longer you make it.

As I just said in another thread, as kernel development continues, the ext4 filesystem becomes less and less attractive. Use ext3 for now. You probably wouldn't notice the benefits between ext3 and ext4 in most cases so, for the moment, it's best to stick with ext3.

Dear sdennie,
please can you elaborate a bit more? I'm about to format a 1 Tb hard disk to ext something and I don't want to get the wrong one and lose all my data.

I've read this: [http://en.wikipedia.org/wiki/Ext4#Delayed_allocation_and_potential_data_loss]("http://http://en.wikipedia.org/wiki/Ext4#Delayed_allocation_and_potential_data_loss")

Does that mean it's alright if I use the newest kernel on Jaunty? How does that compare with how easy it is to lose data on ext3? I can't remember ever losing data on ext3 and it my laptop crashes a lot.

---

### Post by theozzlives on 2009-04-15
I've had complete blackout/brownouts on my test machine and ext4 has held up fine. I'm currently running it on my laptop and it's much faster.

---

### Post by night_fox on 2009-04-15
Well I'm still using Intrepid and it doesn't give me the option of ext4, so I've used ext3. I might upgrade it later.

---

### Post by sdennie on 2009-04-15
In reality, I think ext4 is a great filesystem.  It's going to replace ext3 and I think rightfully so.  It's very fast.  But, it's only recently been declared stabe and I don't think it can live up to what it is.  So, if you are about to partition a TB of data, use ext3.  On a data drive where you are just doing lots of non-important reads and writes you literally won't know the difference.  Use ext3 and know that ext4 could be in your arsenal one day.

---

### Post by MontelEdwards on 2009-04-29
> **sdennie said:**
> In reality, I think ext4 is a great filesystem.  It's going to replace ext3 and I think rightfully so.  It's very fast.  But, it's only recently been declared stabe and I don't think it can live up to what it is.  So, if you are about to partition a TB of data, use ext3.  On a data drive where you are just doing lots of non-important reads and writes you literally won't know the difference.  Use ext3 and know that ext4 could be in your arsenal one day.
right, i agree with you.
this basically is saying "use the most mature fs or program on important, and test on non important

---

