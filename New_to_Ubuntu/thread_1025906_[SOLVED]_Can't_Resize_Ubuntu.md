---
title: "[SOLVED] Can't Resize Ubuntu"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2008-12-30
Okay, I just installed Ubuntu Intrepid in a dual-boot with Vista (Home Premium SP1) on my computer and am loving the experience. The problem is just that though. I never thought that I would like it so much so, when I installed Ubuntu, I didn't think that I needed (or would ever want) more than 10GB of space for the Ubuntu partition. Now, after using it for a month, I only have 4GB left for programs in Ubuntu (I store music and documents on the 93GB Vista partition).

I would like to add between 5 and 10GB of space to Ubuntu but, nothing I try lets me shrink Vista. When I use Vista's tool, it tells me that access is denied after trying to shrink the disk. As for Easeus Disk Paritioner, when I restart I am told that there is an error with the disk when, if I check in Vista, there are none.

My partition scheme is as follows (these are in order as well):

93GB for Windows and any shared documents; 10GB for Ubuntu (home and /); and 8GB for HP Factory Backup (all primary partitions)
If anyone can help I would greatly appreciate it.

---

### Post by dubhear on 2008-12-30
get partition editor

go to applications->add/remove...(applications)

->search for partiotion editor

---

### Post by Martin Marshalek on 2008-12-30
I guess I should have mentioned that...

I have already tried the partition editor for ubuntu and gParted from the install CD. While in Ubuntu, if I try to resize I get a mounting error and the LiveCD just won't let me do anything.

---

### Post by avtolle on 2008-12-30
Try defragging the Vista partition then see if the Vista tool will resize it.

---

### Post by neu2buntu on 2008-12-30
also right click on disk (c) to bring up properties>tools>check now>tick both options>start and then as avtolle said defrag

---

### Post by kansasnoob on 2008-12-30
> **avtolle said:**
> Try defragging the Vista partition then see if the Vista tool will resize it.

+1

A Vista partition should only be resized with Vista's own tools!

There has to be a way!

One silly thought: 

While you're in Ubuntu install Gparted:

```
sudo apt-get install gparted
```

Then you'll find it in System > Administration > Partition Editor. Make sure just before you restart that SWAP is "off".

That is: Close all apps in Ubuntu (including your browser), then go to Partition Editor, right click on SWAP, and select swapoff!

Then restart and try Vista's tools again.

---

### Post by Martin Marshalek on 2008-12-30
Good news! I was able to shrink Vista using error checking (CHKDISK) by 6GB. That's all well and fine but now I can't grow the Ubuntu partition. 

I think I know what the problem is:

As the picture attached shows, the unallocated space is to the left of my Ubuntu partition which is where the data in my Ubuntu install is stored. Therefore, I cannot expand Ubuntu without the unallocated space being to the right of the Ubuntu partition.

If I am correct then that means I need to move the Ubuntu partition over, somehow. How do I do that without reinstalling Ubuntu or Vista?

---

### Post by mkvnmtr on 2008-12-30
Ok you need to be on the live disk to do this. Your Ubuntu is in the /dev/sda5 partition correct? That partition is locked. Find where to click on swap off and it will unlock that partition. Swap off is under device or view I always forget and have to look for it. Then you will be free to enlarge the partition.

---

### Post by Martin Marshalek on 2008-12-30
Yes, my Ubuntu partition is /dev/sda5 however this picture is not from the liveCD. In the liveCD the partition is not locked (none are) and I am allowed to shink the partition put I cannot expand it in the direction of the unallocated space. I can't change the size to be larger. The picture was just to show the partition setup. Sorry, I guess I should have specified.

By the way... Thanks to everyone who has helped I have been trying to do this for weeks but never even got this far.

Or, would I have to format the unallocated space to ext3 and then merge the Ubuntu partition with it? If so, how would I do that?

---

### Post by mkvnmtr on 2008-12-30
Okn when you click on the partition and then click resize you should get a windo that pops up. In it there should be three boxes . One should have a number with the space to the next partition to the right. Another should have the distance to the partition to the left and the one in the center should be the size of the partition in question.Beside the number there should be an arrow up and one down. If you hold the arrow up does the partition not get larger.?

---

### Post by balloooza on 2008-12-30
Try downloading and burning,
[http://sourceforge.net/project/showfiles.php?group_id=248002&package_id=302801&release_id=648596](http://sourceforge.net/project/showfiles.php?group_id=248002&package_id=302801&release_id=648596)
use the iso (first link) it is what helps me when I am resizing, no complex packeges, it allways works, then you can enjoy more ubuntu, It has the same partitioner you are using, eccept it has all the needed files to resize windows partitions, and even mac journaling filesystems.

---

### Post by mkvnmtr on 2008-12-30
That is good information. I had heard that GParted could now work on Vista. That would be a newer version than is on the 8.04 disk but would it be the same as on the 8.10 disk? Why don't you tell us about your experience using it I think a bunch of Vista users would like to here.

---

### Post by raistlyn on 2008-12-30
When installing ubuntu it should of given you the option to use the windows NTFS format version.  Ubuntu usually uses the ext3 format version.  This would eliminate alot of problems and allow both OS's to use he same available disk space.  My suggestion is to reinstall ubuntu "INSIDE" of windows and have it use the NTFS format.

---

### Post by Martin Marshalek on 2008-12-31
You're right, that's all I had to do, sort of. I needed to first resize the /dev/sda3 partition (extended that contains /dev/sda5 which contains Ubuntu) to contain the unallocated space and *then* grow /dev/sda5. I believe the partition is now 16GB (because gParted and Vista tell me that it's 16 GB but, for some reason gParted said there was some kind of error and I still only have 4GB of free space in Ubuntu when I go into nautilus (gParted also tells me that I have 11GB used on that partition (which is impossible because I only had 10GB before. 

So my question is, how do I get the 6GB that I should have for Ubuntu (which should give me 10GB of free space)? Did gParted fail only slightly too early and now there are duplicates and backups of everyting (and I have tried *sudo apt-get clean* and *sudo apt-get autoremove* to see if it would remove the extra stuff)? Did gParted not actually resize the partition and everything thinks that it did. Is the only way to get those 16GB to reinstall Ubuntu (which I could do as the only thing that was hard to do was configure nvidia)? If so, how would I reinstall Ubuntu?

I just saw the other posts before me as well and yes gParted works perfectly with Vista (at least from the Intrepid liveCD). I haven't tried to mess with Vista with gParted but as for Vista working after using gParted for anything (resizing Ubuntu), it does. 

Also, if I have to do more resizing I will use Parted Magic since it sounds perfect.

---

### Post by Martin Marshalek on 2008-12-31
So I finally got the extra space by reinstalling Ubuntu. It was probably a freak error with gParted that didn't keep the extra space and would probably work for anyone who tried this method.

If anyone uses this post to solve a similar problem, and needs a third-party partitioner for vista, I recommend Easeus Home Edition (which is free) that can be downloaded from [http://www.partition-tool.com/personal.htm]("http://www.partition-tool.com/personal.htm").

---

### Post by DanteG on 2009-01-08
> **mkvnmtr said:**
> Ok you need to be on the live disk to do this. Your Ubuntu is in the /dev/sda5 partition correct? That partition is locked. Find where to click on swap off and it will unlock that partition. Swap off is under device or view I always forget and have to look for it. Then you will be free to enlarge the partition.
This post REALLY helped me! Thanks a bunch!!

I partitioned my 60Gb drive in 2 equal partitions for Vista/Ubuntu DualBoot & after installing all applications & updates on Vista I came really close to running out of space on that partition (8.85Gb free) & realized Ubuntu wouldn't be needing 27.9Gb for it to run. Came across a couple of good threads here (This one included :D) that helped me decrease the Ubuntu partition & increase Vista's partition. Indeed in GParted the swap partition needs to be turned off to allow resizing the complete partition. Otherwise GParted will only allow for the Ubuntu partition to be resized.

---

### Post by Gaud3t3 on 2009-01-29
is there an easier way to resize the partition without having to reinstall ubunutu? btw, perfect disk is another great alternative to shrinking and defragging vista. there is 30 day free trial period.

---

