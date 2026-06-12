---
title: "Removed everything and still have hundreds of MB used!"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by KIAaze on 2009-05-01
Hi,

I just wiped my hard drive clean by moving everything onto another PC.
But when I run "df -h" now, it tells me that 129MB are still in use on the /home partition and 196MB on my windows partition. (root partition is separate, I did everything from a vitual terminal logged in as root)

How is this possible?

I removed everything including hidden files.

P.S: rm -rfv WINDOWS was very satisfying. :)

---

### Post by xpod on 2009-05-01
I wouldn`t stand for it,i`d take Gparted to the lot.

That`ll show it who`s boss.;)

---

### Post by arashiko28 on 2009-05-01
Perhaps it has some unallocated data, did you cleaned up the recycle bin?
Why don't you just format it?
Hard drives are never clean enough unless they're virgins and sill has something written on them.
If you want to really get rid of the data, either you can physically destroy it or with one big magnet make it unrecognizable or get one of those programs to really clean up the data.

---

### Post by KIAaze on 2009-05-01
> I wouldn`t stand for it,i`d take Gparted to the lot.

That`ll show it who`s boss.
Yes, but that was just the post-backup fun part. :)

> Perhaps it has some unallocated data, did you cleaned up the recycle bin?
There's no recycle bin left. Not even .gvfs (I used "umount gvfs-fuse-daemon").

I'll reformat during reinstall obviously.
I just found this a bit strange.

---

### Post by llamabr on 2009-05-01
navigate to that directory, and run

```
du -h
```

---

### Post by Jive Turkey on 2009-05-01
It could just be the file system overhead.  Even though there are no files on the HDD, the filesystem itself takes up some space with whatever indexing/journaling information, I don't claim to know all of the specifics.

---

### Post by KIAaze on 2009-05-01
> **llamabr said:**
> navigate to that directory, and run

```
du -h
```

```
$du -h /home
4.0K
$du -h /media/hda1 (windows)
24K 

```
Windows is obviously more bloated, even after removal. :P (or it's just FAT32 vs ext3).

> It could just be the file system overhead. Even though there are no files on the HDD, the filesystem itself takes up some space with whatever indexing/journaling information, I don't claim to know all of the specifics.
Over 100MB seems a bit huge...

Note: No change after unmount/remount of the partitions by the way.

edit:
Found some new info about space inconsistencies:
[http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/](http://www.walkernews.net/2007/07/13/df-and-du-command-show-different-used-disk-space/)
[http://www.chineselinuxuniversity.net/articles/17988.shtml](http://www.chineselinuxuniversity.net/articles/17988.shtml)
[http://books.google.com/books?id=wOGUuoHUyAEC&pg=PA47&lpg=PA47&dq=linux+df+used+%2B+available+does+not+equal+size&source=bl&ots=OEkupul51V&sig=YMNmKvRjl2xoeoJbjXj5rfbeR7I&hl=en&ei=82kBSoXvCMGOsAaVwej0Dg&sa=X&oi=book_result&ct=result&resnum=1#PPA48,M1](http://books.google.com/books?id=wOGUuoHUyAEC&pg=PA47&lpg=PA47&dq=linux+df+used+%2B+available+does+not+equal+size&source=bl&ots=OEkupul51V&sig=YMNmKvRjl2xoeoJbjXj5rfbeR7I&hl=en&ei=82kBSoXvCMGOsAaVwej0Dg&sa=X&oi=book_result&ct=result&resnum=1#PPA48,M1)
[http://ubuntuforums.org/showthread.php?t=1150532](http://ubuntuforums.org/showthread.php?t=1150532)

---

