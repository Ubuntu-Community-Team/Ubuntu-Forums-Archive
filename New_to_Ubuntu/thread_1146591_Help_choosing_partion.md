---
title: "Help choosing partion"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by akrchstn on 2009-05-02
I just made a 20 gig partion for ubuntu but I don't know what option to choose on the installer.  The 8.04 installer was a lot easier than this...So which one should I choose to install ubuntu under the 20 gig partion I made?
[IMG]http://i664.photobucket.com/albums/vv4/akrchstn420/Screenshot.png[/IMG]

---

### Post by Delever on 2009-05-02
"Use largest continuous free space" should do the job.

---

### Post by Didius Falco on 2009-05-02
If you've already created the partition, choose specify **partitions manually (advanced)**, then highlight the partition you created, click the **edit partition** button at the bottom of the partitioner screen, and set the options up to use it and set it to /. If you already formatted it, you can just not format it, but if it is an empty partition, it won't hurt anything.

Then you should be good to go.

---

### Post by presence1960 on 2009-05-02
> **Didius Falco said:**
> If you've already created the partition, choose specify **partitions manually (advanced)**, then highlight the partition you created, click the **edit partition** button at the bottom of the partitioner screen, and set the options up to use it and set it to /. If you already formatted it, you can just not format it, but if it is an empty partition, it won't hurt anything.

Then you should be good to go.

**+1**

This will insure 100% that you use the partition you created for Ubuntu.

---

### Post by -kg- on 2009-05-02
If you did actually create a partition for Ubuntu, then I concur with Didius...use the "Specify Partitions Manually" selection.

However, in your screen shot it shows the (approx) 20 GB space as Free Space, which would indicate to me that you only shrank the Vista partition and cleared up some free space, which would have prompted Delever's reply.

I do notice that you have a swap partition at the very end, though, so it may be that you created a partition but didn't format it.  For myself, I always use Manual partitioning, just because I know what I'm doing [-o< and what I want.

Manual partitioning will work either way, and since you already have a swap partition created, that would be the way I'd go in your case, as well.  I dont' know about Jaunty, but other installers I've tried have created an extra (unnecessary) swap partition, wasting space unnecessarily.  I don't think Jaunty's will, though.

That's what I suggest you do.  All you will have to do is create the main partition in free space, mark it as "/" (at the bottom of the partitioning window) and go forth, since the swap partition is already created (and you don't have to mark it).

Also, read up a little on the following page, which has some good basic partitioning info:

[How To Partition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by anewguy on 2009-05-02
Not only does it show a swap partition, it shows it as 8 GIG!!  Depending on how much system memory you have, you should be able to run with a swap of 512mb.  If it's a laptop, and IF you plan to TRY to get hibernation to work, then you may need UP TO (depends on the laptop) 2 times the amount of physical memory you have, but that would be doubtful.

If this is a desktop, indeed as already recommended, choose the manual partition method.  But before you select use all available space, resize the swap partition down to only about 512mb.  It may be best just to delete the current one and allocate a new one of only 512mb.  Then move on to your primary Linux partition, and remember to select the mount point as "/" on the screen.

Dave :)

---

