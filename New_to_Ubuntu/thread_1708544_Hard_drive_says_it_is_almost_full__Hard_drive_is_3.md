---
title: "Hard drive says it is almost full  Hard drive is 335GB free space"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Peterfc on 2011-03-16
I have just downloaded a movie. I got an error message that i only had 1.9GB free space.I am using 10.10 with no windows my hard drive is 500GB.

When i go to places and down to my hard drive when i click the drive it says free space is 355 GB.

I only have the one partition. I have just done a search for Hard drive full but did not find an answer.

Thanks for taking the time to read my problem.

---

### Post by matt_symes on 2011-03-16
Hi

have a look at your disk usage using (from a terminal)

```
sudo du -ax / | sort -nr | head -n 30
```

That will list the top 30 largest files in your root file system. See what is taking up the room. Check both partitions.

You are definitely saving to your large partition aren't you ?

Kind regards

---

### Post by pqwoerituytrueiwoq on 2011-03-16
not that it is the reason you are posting but you only need 1 swap partition
you can have 10 linux installs using the same swap partition
you just need to keep the UUID correct on /etc/fstab for the swap partition

---

### Post by grahammechanical on 2011-03-16
You actually have four partitions. Two of them are 2.3GB swap partitions. You only need one swap partition even if you install two or more distributions of Linux can can use the same swap partition for each distributions.

What are you using the 396GB partition for? If Ubuntu is in the 99Gb partition and you did not set up a home partition in the 396GB partition but a home folder in the 99GB partition then that partition could indeed be nearly full. It depends on the size of your movies and if you remove them after viewing.

Remember, when you delete a file it still remains on the hard disc taking up space. Deleting a file symbolically moves the file to the rubbish bin. You might want to restore the file. So it is not actually removed from the hard disc until you empty the rubbish bin. You may have put several movies in the rubbish bin and they are filling up your hard disc.

Under System>Administration you will see a utility called Disc Utility. Have a look and see what that shows you.

Regards.

---

### Post by drs305 on 2011-03-16
First, from the screenshot it appears you are only using a 99 GB primary partition as /. The rest is in the extended partition.

You can take a look at a guide I wrote on disk space to help you figure out what is taking up most of your 99 Gigs:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Added: If you have a separate /home partition in the extended partition, your downloads may be winding up in the / partition rather than the larger /home partition.

And when looking for the problem, note that the three most common causes of this problem in my experience has been undeleted trash (including root's), large or 'out of control' log files, and backups made to the wrong partition (i.e. the backup partition wasn't mounted at the time of the backup, so it was placed in one of the / folders).

---

### Post by Peterfc on 2011-03-16
Thanks guys. 

I am at a loss as i didn't know i was not just using one partition. This setup has been running since about the time of Dapper and was updated as and when the upgrades are required. So it is a bit difficult to remember what i originally set the hard drive to when i first installed Ubuntu.

A simple answer to me would be to just have one partition and as mentioned one swap partition. My next question now is how do i do this without doing any harm to my present setup?

Thanks for all your help.

---

### Post by drs305 on 2011-03-16
There are a few things you should probably do from a running Ubuntu.

1. Ensure you don't have a separate /home partition. Run the following command. sda1 will be mounted on /. You probably will see a partition mounted as swap, but what you want to look for is one (sda5) mounted as /home.

If you don't see it, it means that /home is just part of your 99GB partition. If you find a /home or /your-username on an extended partition, don't continue with the following instructions. 

Next, mount /dev/sda5 and make sure it doesn't contain any files:
```
sudo mount /dev/sda5 /mnt
gksu nautilus /mnt
```
Inspect the contents and make sure there isn't anything there.

Once you are sure there is nothing in the extended partition except swap, you can procede to delete these partitions. You will need to do this from a LiveCD, as all the partitions must be unmounted.

Back up your important data. Any partitioning could go wrong and you could lose your files.

Boot a LiveCD and open Gparted (System, Administration, Gparted/Partition Editor).

Click on each swap partition, and from the top menu select Partition, Swapoff (only one may be mounted). There should be no key icons next to any partition in the lower panel (the key icon means the partition is mounted).

You only need one swap partition. I would keep the one on the far right. To delete the earlier one, click on it, then Partition, Delete.

Now, most of us wouldn't recommend just having a single / and a swap partition. Having partitions in an extended partition can be really useful. Things such as a separate /home, a data partition, etc.

But for simplicity I'll describe how to do what you want.

Next, click on sda5 partition and Partition, Delete.

Now you should shrink the Extended Partition (light blue border). Click on the light blue border or on the Extended Partition listing in the bottom panel. Partition, Move/Resize. Now you can slide the left border to the right to shrink it.  Move it all the way to touch the swap partition. 
(Again, this isn't ideal but it will do what you asked for.)

Now expand sda1. Select the partition, then Partition, Move/Resize and expand it by dragging the right border all the way over to touch the light blue border of the extended partition.

In the end, you should see sda1, then within the extended partition - swap.

Click the APPLY button at the top to make the changes. It will take a while for the process to complete as the partitions are resized.

If you aren't sure or want to reconsider having just one partition you can always ask questions. Should you want to add extra logical partitions later it actually won't be too difficult with this configuration.

---

### Post by Peterfc on 2011-03-17
Thanks drs305

I have printed the text from your reply and when i get home from work i will follow your advice. 

Thanks

---

### Post by drs305 on 2011-03-17
It's easier than it appears. Just take your time and ask questions if you need to. The biggest concern should be making sure there isn't anything you want in the partitions you are going to delete.

A picture may make things easier to understand.
[http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by oldfred on 2011-03-17
While drs305 has given good instructions, and mentioned a separate /home or /data, I think at this point that would be a much better way to go. I do not like large system partitions. For newer users I suggest the separate /home and for more advanced users the separate /data with /home still in / (root).

The advantages of a small system partition with separate /home is that a clean new install does not erase your /home (if you tell it not to erase it) and then makes new installs easier. It separates most user data from the system. There is some small advantages of having all the system files located nearer to each other on the drive. And separate partitions will not typically have issues at at the same time so fsck or other repairs are easier. But too small partitions can make reorganizing difficult, so there is some trade-off.

There are a lot of instructions on moving /home:
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

