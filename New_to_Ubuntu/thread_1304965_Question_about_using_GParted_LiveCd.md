---
title: "Question about using GParted LiveCd"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Ricorich196 on 2009-10-29
Okay so I have this plan and I wanted to know if it has any "holes" in it. I currently have a 500GB HDD running 8.10 on a single partition. The disk has about 200 GB free and now I want to do a clean install of 9.10 but I have no external hard drive to back up media files and had this idea.

Would it be possible to use the GParted LiveCD to separate the remaining 200GB into a new partition (let's call this partition B), move all my media files to that partition[B], install 9.10 on the existing partition (The original 275GB or so partition let's call it A), resize partition A to about 100 GB for 9.10 and allocate the remaining space [about 150 GB] on the drive to partition B so that instead of it being 200 GB it'll be 3505 GB.

I know it sounds confusing but hopefully I'm understandable.

Thanks in advance guys!

---

### Post by KIAaze on 2009-10-29
Of course it's possible. But why resize so many times if you can resize only once?:
1) Resize the current partition to the size you want for your data/home.
2) Create a new partition on the remaining space.
3) Install Ubuntu on the new partition.

And you do understand that **there's no guarantee you won't loose your data**, right?
I suppose that the more you resize, the bigger the risk of losing data.

Personally, I never had data loss when using GParted so far, but that doesn't mean it can't happen.

Also, GParted is available on The Ubuntu Live-CD if I remember correctly. In case you don't have the GParted Live-CD with you one day. ;)

P.S.: 100 GB is really huge just for Ubuntu. Do you plan to install all available packages? ^^
I settled for 20 GB on my desktop and 10 GB on my laptop for the / partitions. 5 GB is theoretically enough, but not if you install lots of packages.

> I currently have a **500GB** HDD. ... Would it be possible to use the GParted LiveCD ... so that instead of it being 200 GB it'll be **3505 GB**.
Sorry, no, this is impossible with our current technology. :lol:

---

### Post by Ricorich196 on 2009-10-29
> **KIAaze said:**
> Of course it's possible. But why resize so many times if you can resize only once?:
1) Resize the current partition to the size you want for your data/home.
2) Create a new partition on the remaining space.
3) Install Ubuntu on the new partition.

And you do understand that **there's no guarantee you won't loose your data**, right?
I suppose that the more you resize, the bigger the risk of losing data.

Personally, I never had data loss when using GParted so far, but that doesn't mean it can't happen.

Also, GParted is available on The Ubuntu Live-CD if I remember correctly. In case you don't have the GParted Live-CD with you one day. ;)

P.S.: 100 GB is really huge just for Ubuntu. Do you plan to install all available packages? ^^
I settled for 20 GB on my desktop and 10 GB on my laptop for the / partitions. 5 GB is theoretically enough, but not if you install lots of packages.


Sorry, no, this is impossible with our current technology. :lol:

Lol typo sorry. The reason for resizing so many times was how could I resize the current partition that has ALL my data AND move my media to a separate partition without losing anything? I mean in my mind I'd imagine if I resized my current partition (over 300 GB of data mostly media) and made it smaller I'd end up losing everything, no?

---

### Post by phillw on 2009-10-29
> **Ricorich196 said:**
> Okay so I have this plan and I wanted to know if it has any "holes" in it. I currently have a 500GB HDD running 8.10 on a single partition. The disk has about 200 GB free and now I want to do a clean install of 9.10 but I have no external hard drive to back up media files and had this idea.

Would it be possible to use the GParted LiveCD to separate the remaining 200GB into a new partition (let's call this partition B), move all my media files to that partition[b], install 9.10 on the existing partition (The original 275GB or so partition let's call it A), resize partition A to about 100 GB for 9.10 and allocate the remaining space [about 150 GB] on the drive to partition B so that instead of it being 200 GB it'll be 3505 GB.

I know it sounds confusing but hopefully I'm understandable.

Thanks in advance guys!

As pointed out ....
10GB is plenty for the ubuntu installs, you'd be pushed to use that much !!
you want 1GB for swap (for upto 1GB RAM, if more than 1GB RAM use SWAP GB = RAM GB)
So, that's 22 GB .... hmmm 478 to go
make a partition called, say, /data and have that at, say, 400 GB
make a partition called, say, /backup with the rest of the disk.

you can then use a simple backup script like this ... [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

to have 2 scripts that will backup the 'core' of your 2 ubuntu installs - so you can 'play' in safety. (Don't have the same filename as the output from the 2 systems !!!!)

Or, you could have, say, 225GB as /backup and the remainder as /data if you prefer to backup your data - although, tbh - I'd use a seperate disk for that.

Well, that's some more ideas to have a think about. Other ones include a seperate /home partition etc..

Regards,

Phill.

---

### Post by phillw on 2009-10-29
> Lol typo sorry. The reason for resizing so many times was how could I resize the current partition that has ALL my data AND move my media to a separate partition without losing anything? I mean in my mind I'd imagine if I resized my current partition (over 300 GB of data mostly media) and made it smaller I'd end up losing everything, no?

No, you wouldn't lose any data - provided you don't try to resize the partition to be SMALLER than the amount of data stored on the partition.

Phill.

---

### Post by Ricorich196 on 2009-10-29
Gosh, now I'm really confused. So I'd need probably 25 GB for a new Ubuntu installation, I want a second partition strictly to hold my media but everything is jumbled onto 1 partition. Maybe I can make 2 partitions 1 25GB for 9.10, another for my media to back up to, then erase the original partition, then expand the media partition to take advantage of the new acquired space I got from erasing the original partition.

---

### Post by KIAaze on 2009-10-29
My suggestion was to just reduce the size of the existing partition to make place for a new partition on which to install Ubuntu.
You don't need to create a new partition for your media.
Once you've installed Ubuntu on another partition, you can just delete everything except your media on the old partition (boot into the newly installed Ubuntu, mount the old partition and do with it as you please).

The only drawback would be that you would have space left on the old/media partition. But isn't that desirable for a media partition?

Of course, since you have 500 GB, you can create more than 2 partitions if you want and be creative. :)
You could create a /boot partition to share the boot files between different distros for example.
A separate home partition is probably the most useful thing to have.

---

### Post by Ricorich196 on 2009-10-30
> **KIAaze said:**
> My suggestion was to just reduce the size of the existing partition to make place for a new partition on which to install Ubuntu.
You don't need to create a new partition for your media.
Once you've installed Ubuntu on another partition, you can just delete everything except your media on the old partition (boot into the newly installed Ubuntu, mount the old partition and do with it as you please).

The only drawback would be that you would have space left on the old/media partition. But isn't that desirable for a media partition?

Of course, since you have 500 GB, you can create more than 2 partitions if you want and be creative. :)
You could create a /boot partition to share the boot files between different distros for example.
A separate home partition is probably the most useful thing to have.

How would I go about deleting everything off the old partition except my media.

---

### Post by KIAaze on 2009-10-30
Maybe you misunderstood me. You don't delete data with GParted, you delete it with nautilus or by command-line after mounting the partition.

So you just delete it manually.
ex:
```
sudo mkdir /media_backup
sudo mv media_1 /media_backup
sudo mv media_2 /media_backup
...
sudo mv media_N /media_backup
sudo rm -rf /boot /etc /home ...

```

Note: You can actually delete unnecessary data before or after resizing with GParted.

---

