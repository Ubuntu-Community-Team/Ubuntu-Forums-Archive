---
title: "Do we have to de-frag in ubuntu like we did in windows?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-15
I have 3 computers and they are all now running ubuntu. Bye-bye windows ):P

Quick question though, do we have to de-frag like we did in windows?

(I used to do that once a week back in my vista days)

Thanks

---

### Post by bgates on 2009-02-15
My understanding is that while defrag tools do exist, they generally aren't needed since Ubuntu does not tend to create fragmentation.  It may vary according to which filesystem is used.  I had planned to spend a while installing and uninstalling applications and things first, then get one of the tools and scan with it to see what, if any, fragmentation I have.

---

### Post by perlluver on 2009-02-15
Be careful with Defrag tools in Ubuntu, they can cause harm.  To the Original Poster, I wouldn't worry about defraging, I haven't defraged since I have installed Ubuntu, and it seems to be pretty fast still.  [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812), I would recommend taking a look at that.  It does a good job of explaining.

---

### Post by listerdl on 2009-02-15
Thanks....ill check out the link

---

### Post by Kellemora on 2009-02-15
Hi List

It really depends upon which file system you are using for your data files.

EXT3 is like pigeonholes, you edit a file, it gets shoved back in the same pigeonhole.  Most used files get stored close to the heads, least used files end up in the south forty.  Clean, neat and fast.

NTFS is like a string of beads, you edit a file and it sticks the edited part at the end of the string of beads, so each time you edit a file, or a file changes, those changes get stuck at the end.  Many files change that you may not think changes, but they do.  So basically, on an NTFS hard drive, it simply keeps going from bad to worse and requires constant defragging to speed it back up again.
When you defrag it moves the files back together again, by first making space and then reading the files and lining the beads all back up again, hi hi.....

However, even though we still use NTFS for a few things, there is a faster way to keep the drives in shape than running defrag.  We will simply copy whole folders from the server or from one partition to another.  This lines them all back up again too!  And is usually considerably faster than defrag.

TTUL
Gary

---

### Post by ibuclaw on 2009-02-15
File fragmentation being the cause of a bottle-neck in Linux is unheard of. Though if you have, say a 95% filled hard-drive and are constantly appending and truncating files, then there is a chance of that happening.

But in truth, it's generally not a worry because system files tend to stay static on the disk, and if you update some? Well, the default Ubuntu filesystem (ext3) as well as other Linux filesystems ensure that data writeback is optimal, as in it ensures that files written to disk are spread out across the filesystem, so they are able to grow/shrink with minimal chance of fragmenting in the process, so you may find that your system will be just as fast 2/3 years down the line as when you first ran it ;)


As an example of the filesystem working, there is a utility called **filefrag** which counts the number of extents a file is in.
ie:
[PHP]
$ sudo filefrag ubuntu-8.10-desktop-i386.iso 
ubuntu-8.10-desktop-i386.iso: 462 extents found
[/PHP]
An ISO-Image that is in 462 fragments.

Now, I'll make a copy of that file and test the number extents in the new version.
[PHP]
$ cp ubuntu-8.10-desktop-i386.iso ubuntu-8.10-desktop-i386.iso.new
$ sudo filefrag ubuntu-8.10-desktop-i386.iso.new 
ubuntu-8.10-desktop-i386.iso.new: 182 extents found
[/PHP]
182 extents found. The filesystem has ensured that the file has been allocated space on the disk in the most efficient way, and by chance the new file is in less fragments too.
[PHP]
$ mv ubuntu-8.10-desktop-i386.iso.new ubuntu-8.10-desktop-i386.iso
$ sudo filefrag ubuntu-8.10-desktop-i386.iso 
ubuntu-8.10-desktop-i386.iso: 182 extents found
[/PHP]
jdong, one of the old users of these forums actually wrote a defragmenter in python that worked in this near exact way. But apart from learning that the filesystem is your best protection against fragmentation, you really don't need to get your mind bogged down on the issue. As there really isn't anything to find on the subject. :)

Regards
Iain

---

### Post by gn2 on 2009-02-15
If you use the default ext3 filesystem you don't need to de-frag.

Here's what Wikipedia has to say: [http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation)

---

### Post by SunnyRabbiera on 2009-02-15
The answer is no, most linux filesystems have much cleaner allocation then windows.
As far as I know the common ext3 filesystem (the default most linux distros use including Ubuntu) only fragments when space begins to run out, I believe it kicks in when there is about 6% of the drive left...
Or something, but I would not worry about it if your hard drive has over 20GB of space.

---

### Post by Amenhoteph on 2009-02-16
Drive frag is a nice artifact from the mainframe days that the boys at Microcrap decided to preserve for future generations.  Just file it away as yet another thing that you don't have to worry about anymore.

---

### Post by HermanAB on 2009-02-16
Uhmmm, actually, you need not defragment Windows NTFS either - for the same reasons.  NTFS is quite a good file system.

Cheers,

Herman

---

### Post by Crafty Kisses on 2009-02-16
You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean
```

---

### Post by joey-elijah on 2009-02-16
> **Kellemora said:**
> 

EXT3 is like pigeonholes, you edit a file, it gets shoved back in the same pigeonhole.  Most used files get stored close to the heads, least used files end up in the south forty.  Clean, neat and fast.

NTFS is like a string of beads, you edit a file and it sticks the edited part at the end of the string of beads, so each time you edit a file, or a file changes, those changes get stuck at the end. 

TTUL
Gary

What an awesome way to describe it! I've learnt something today, thank you! I almost want to change my shared partition to EXT3 now!

---

### Post by Tony Flury on 2009-02-16
> **Codename said:**
> 
There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean
```

that command does not "clean" the entire file system - it cleans the apt-get package cache (by deleteing cached package files and updating some lists). So nothing like defrag.

from man apt-get
```

       clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

```

---

### Post by randalph on 2009-02-17
Please stop repeating the myth that ext3 (or any filesystem) is impervious to fragmentation or that it is rare. Multiple simultaneous write streams can induce fragmentation on ext3. Getting close to filling up the drive can induce fragmentation on ext3. Those might be less frequent events than typical uses but they are not theoretical, and unfortunately when it happens there's no defrag utility so there's nothing you can do about it except start over. Not having a defrag utility and being better than FAT32 is not the same thing as defrag not being necessary. With ext3 my Ubuntu box running MythTV eventually got fragmented to the point that it was significantly affecting playback. There was plenty of free space but the multiple write streams & multiple close-to-full events over the (brief) lifetime of the box caused new files to be written with many extents. (I ran a test with 10+ GB free, a freshly written much smaller file in a new directory was spread over many extents). This was a 500GB drive, about a 1 year old since the original format. This caused unavoidable playback stutters. The "fix" was to format a drive as XFS and clone the system. Lesson learned - all my systems are XFS now.

Those of you claiming there is no fragmentation kindly post representative filefrag results on their 2-3 year old ext3 daily-use drives.
[http://prefetch.net/blog/index.php/2007/01/21/determining-file-fragmentation-on-ext3-file-systems/](http://prefetch.net/blog/index.php/2007/01/21/determining-file-fragmentation-on-ext3-file-systems/)

Use XFS and an online defragment cronjob if you don't want to have to deal with fragmentation.
[http://www.mythtv.org/wiki/XFS_Filesystem](http://www.mythtv.org/wiki/XFS_Filesystem)

---

### Post by Jingle on 2009-02-17
> **HermanAB said:**
> Uhmmm, actually, you need not defragment Windows NTFS either - for the same reasons.  NTFS is quite a good file system.

Cheers,

Herman

Could you go into a bit more detail on this one please?  My shared volumes are NTFS (access by XP/vista machines too) and they are fragmented to hell.

I presume the best thing is to boot into windows and defragment those partitions from there?

---

### Post by Kellemora on 2009-02-17
Hi Jingle

I use a Data File Server, it is formatted in EXT3, this is where all the files get read from and written to all day long, big files, little files, all files.

The Data File Server is mirrored to an NTFS drive using Rsync.  And even though we are not reading and writing to it, it gets highly fragmented as changed files are copied over to it.

I'm no guru, but it appears to me that each change made to a file is added to the end and a flag placed to tell the drive or computer, part A of file is in sector so n so and part B of this file is in sector so n so.  However it works, the changes are always stuck to the end of the string of beads.  So when retrieving this file, the heads may have to start at point A, jump to B, C, D, E and so on and so forth until it has collected all the pieces of that file.

I made two partitions on the mirrored drive, both NTFS (we have a reason for using NTFS on the Mirror), and simply by copying Partition A to Partition B, it defrags itself without the time consuming defrag program.
I assume this is because it reads a file, collects it's separate parts, then writes it to the next partition in order as a single file again.

I started doing it this way back in my WinDoze Daze, because it was exponentially faster than running defrag and the end result was the same.
You could view the drive with a defrag tool and see it was clean and tight with no fragmentation.  Also, theres little to no chance of total data loss using a copy command vs defrag.  We work with monstrous size image files, and using defrag sometimes causes an image file to become unreadable.  This happens using copy also, but very very rarely.
Because of our redundant backups/mirrors and mirrors without using the --delete command in the code, we can usually retrieve a corrupted file.

Defrag works by clearing space at the beginning of the string of beads, moving files to the end of the string, then starts copying files to fill the new empty space, if space runs out because the next file is too big, it moves the next file to the end, then returns to filling the empty space again.  If you use a GUI type of defrag tool that shows whats going on, you can actually watch it do this.  Much easier in the old days when the drives were smaller and showed nearly each sector, hi hi.......
In other words, defrag moves files back and forth, sometimes several times before it completes.

When you do use the copy though, you want to use a clean drive, copying to a drive you already copied those files to once already will not afford much in the way of defragmentation, because it will write to the existing file until full then add the rest to the end of the string of beads.
So erase the drive you will be copying to, then run the copy.
It may take 6 hours to run defrag, but only about 15 minutes to copy the same amount of data.  Depending on source and destination and path taken too of course.

All of the Windows machines can read the data file servers EXT3 stored files because they are going across a LAN, the DOZE has no idea what file system is in use on the data file server and don't care.  The reason we make the mirror NTFS is because if the office burns down, we will only have two Doze machines at POS to access data from until we are back up and running again with Ubuntu.  Plus our accounting machine is still using the DOZE.....  Just a point of security or safety with us is all!
But even the Doze reads from the EXT3 file server over LAN FASTER than reading from and NTFS external USB drive!

TTUL
Gary

---

### Post by jerome1232 on 2009-02-17
Fragmentation generally isn't a problem with ext3 unless your drive is full. All my ext3 drives sit at around .9% fragmentation.

If an ext3 file system becomes fragmented you do not have to "start over" just move the files off the file system then move them back on, it will defragment the files.

I have had ext3 become fragmented heavily once, it hit 20% fragmentation because my torrent client didn't allocate space for files it just wrote them piece by piece. I set the client to allocate the space and moved the files off/on the file system and bingo back down to .7% fragmentation and it hasn't climbed since.

ext4 will have an online defragmenter so that's good news for those who need it. :)

---

### Post by barney_1 on 2009-02-18
> **randalph said:**
> Please stop repeating the myth that ext3 (or any filesystem) is impervious to fragmentation or that it is rare. Multiple simultaneous write streams can induce fragmentation on ext3. Getting close to filling up the drive can induce fragmentation on ext3. Those might be less frequent events than typical uses but they are not theoretical, and unfortunately when it happens there's no defrag utility so there's nothing you can do about it except start over. Not having a defrag utility and being better than FAT32 is not the same thing as defrag not being necessary. With ext3 my Ubuntu box running MythTV eventually got fragmented to the point that it was significantly affecting playback. There was plenty of free space but the multiple write streams & multiple close-to-full events over the (brief) lifetime of the box caused new files to be written with many extents. (I ran a test with 10+ GB free, a freshly written much smaller file in a new directory was spread over many extents). This was a 500GB drive, about a 1 year old since the original format. This caused unavoidable playback stutters. The "fix" was to format a drive as XFS and clone the system. Lesson learned - all my systems are XFS now.

Those of you claiming there is no fragmentation kindly post representative filefrag results on their 2-3 year old ext3 daily-use drives.
[http://prefetch.net/blog/index.php/2007/01/21/determining-file-fragmentation-on-ext3-file-systems/](http://prefetch.net/blog/index.php/2007/01/21/determining-file-fragmentation-on-ext3-file-systems/)

Use XFS and an online defragment cronjob if you don't want to have to deal with fragmentation.
[http://www.mythtv.org/wiki/XFS_Filesystem](http://www.mythtv.org/wiki/XFS_Filesystem)

Yes, yes, and furthermore, yes!  I use XFS for my mythbuntu setup but I did not have the on-line defrag set to run automatically.  I started to have incredible stutter when watching over the network and chased the problem down to fragmentation.  When I checked my fragmentation with xfs_db I got this:
```
actual 190020, ideal 6098, fragmentation factor 96.79%

```

97% fragmented!?!  No wonder I'm having problems with a normally fast system.  I use xfs_fsr to clean this up and get rid of my performance issues.

---

### Post by randalph on 2009-02-21
Actually I'm a huge liar - I still have an ext3 partition on a laptop that I dusted off for test 1 below. I invite everyone to try the tests for themselves. Mine was formatted ext3 in 2006 and Ubuntu 6.04 was installed. It has a a 20GB partition for / with 2.6GB free before I began the test.  It's been upgraded over the years and is now running 9.04 alpha 4, but has been a backup machine & has been mostly sitting on a shelf since mid `08. When on, it has been subject to typical power user but not over-the-top laptop usage patterns; firefox, gcc/misc development, gimp, open office. no MythTV. 

TEST 1a:
I created a 300MB file with:
> dd if=/dev/zero of=/tmp/testfile1 bs=1M count=300
then I tested the fragmentation with: 
> sudo filefrag /tmp/testfile1
result: "186 extents found, perfection would be 3 extents"

TEST 1b:
to test the claim by some that you need only copy the file to a new one with sufficient free disk space:
> cp /tmp/testfile1 /tmp/testfile2
> sudo filefrag /tmp/testfile2
result: "74 extents found, perfection would be 3 extents"

commentary: the file fragmented and there's no low cost fix. moving all the data off the drive so that it's empty then moving it all back on /is/ starting over, not to mention a PITA. If my seek time is 10ms that's 1.86s/0.74s respectively that is wasted jumping around the drive when reading those files in the future. fresher drives and/or more free space may very well result in a single extent with this specific test, but my point is once ext3 does start fragmenting, there's no a simple fix that's lower cost than just using a defragmentable filesystem in the first place. Also note that fragmentation reported by fsck underreports the value due to the number of 0-byte files ([http://www.h-online.com/open/Tuning-the-Linux-file-system-Ext3--/features/110398/3](http://www.h-online.com/open/Tuning-the-Linux-file-system-Ext3--/features/110398/3))

TEST 2:
next I ran this test on an XFS formatted root drive on my current daily-use laptop (60GB total, 34.4GB free, 0.73% fragmentation according to xfs_db, drive is defragmented nightly with a xfs_fsr cronjob):
> `dd if=/dev/zero of=testfile1 bs=1M count=300 &`;`dd if=/dev/zero of=testfile1 bs=1M count=300 &`
> sudo filefrag /tmp/testfile1; filefrag /tmp/testfile2;
result: 31 extents found in the first, 60 in the second.

note that even with over half the drive free and very low existing drive fragmentation, two simultaneous write streams will cause fragmentation. This is even true for my beloved XFS.

then: 
> sudo xfs_fsr -v /tmp/testfile1 /tmp/testfile2
> sudo filefrag /tmp/testfile1; filefrag /tmp/testfile2;
result: both files are reported to now have 1 extent

commentary: ever download 2 things at the same time? I have. With XFS fixing fragmentation for real, automatically, in the background, without having to know which files are fragmented, is a snap. I'm sorry but the suggestion that Ubuntu users should first identify when fragmentation has become an issue and then have to periodically manually move /all/ data off a drive, then back on, just to get rid of fragmentation is pretty ridiculous for 2009.

I implore you all; run a defragmentable filesystem & set a defragment cronjob. Or at least stop contributing to the problem by telling people that defragmentation is not necessary.

---

### Post by jerome1232 on 2009-02-21
Well I dunno I seem to exhibit quite opposite behavior, the file becomes heavliy fragmented when I copy it to my nearly full partition and very unfragmented when it copies to my partition that's got a good amount of free space.

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/direbane-UbuntuRoot
                       15G  7.6G  6.5G  54% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  352K  500M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.9M  498M   1% /dev
tmpfs                 501M  524K  500M   1% /dev/shm
lrm                   501M  2.4M  498M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/mapper/direbane-UbuntuHome
                       30G   25G  3.7G  88% /home
/dev/sda1             274M   63M  212M  23% /boot
/dev/mapper/direbane-data
                       99G   68G   32G  69% /media/torrents
/dev/mapper/direbane-wow
                       40G   14G   25G  36% /media/World of Warcraft
/dev/scd0             3.1G  3.1G     0 100% /media/cdrom0

ls -lh /media/torrents/Swing\ Vote.iso 
-rw-r--r-- 1 jeremy jeremy 2.6G 2009-01-29 00:43 /media/torrents/Swing Vote.iso
sudo filefrag /media/torrents/Swing\ Vote.iso 
[sudo] password for jeremy: 
/media/torrents/Swing Vote.iso: 27 extents found, perfection would be 22 extents
mv /media/torrents/Swing\ Vote.iso ~/
sudo filefrag /home/jeremy/Swing\ Vote.iso 
[sudo] password for jeremy: 
/home/jeremy/Swing Vote.iso: 305 extents found, perfection would be 22 extents
mv /home/jeremy/Swing\ Vote.iso /media/torrents/
sudo filefrag /media/torrents/Swing\ Vote.iso 
[sudo] password for jeremy: 
/media/torrents/Swing Vote.iso: 27 extents found, perfection would be 22 extents
```

the partition with space to work with no real fragmentation, partition with no free space to really work with becomes heavily fragmented. I agree with you that online defragers are nice, xfs and ext4 both have one. So defrag away if your having speed hits due to fragmentation. I certainly had a speed hit copying to my quite full /home vs copying to my very empty /media/torrents. Looks like it's time for me to resize /home :)

---

### Post by Kellemora on 2009-02-21
Hi Randalph

I think you're missing something here!

The pigeonholes are of a fixed size.
If you try to save a file larger than the pigeonhole, it still saves the file sequentially but in two or more pigeonholes, depending upon the file size. So it's going to show that file as fragmented, even though its really sequential which is just what you want for speed.

If you edit the file, it gets put back right where it was read from, extra data does NOT get stuck elsewhere on the drive as in the NTFS file system.

In NTFS, if you edit the same file 30 times, you will have 30 instances of fragmentation as each edit gets added to the end of the string of pearls.

In EXT3, if you edit the same file 30 times, you will still have the number of fragmentations the same unless you spread over into yet another pigeonhole.  So the count would go up by only 1.  If the file is smaller than the pigeonhole, no matter how many times you edit it, it won't show as fragmented.

If you copied a file to a formatted hard drive and it's showing that file as fragmented, then it's because the file is larger than a single pigeonhole and is spread out across sequential pigeonholes.

We work with really huge image files, and I can place a single image on a newly formatted hard drive and it will show it as being fragmented, sometimes as many as 8 to 12 times.  Which I hope you realize is impossible, it's the only file on there and runs from location point A beginning to location point B end with no points used in between.

If I edit the image and save it back, it still has the same starting point and perhaps the file is larger or smaller and is given a new location point B end point.

Try that NTFS and you do end up with a fragmented file, point A to point B PLUS point E to point F.  Edit again and you have point A to point B, PLUS point E to point F, plus point J to point K.  If working with two images and going back and forth between them.

That don't happen at all on the EXT3 file system!  

TTUL
Gary

---

### Post by randalph on 2009-02-21
Hi Kellemora: With all due respect I think you are the one who is missing something. I don't see why what I'm saying is controversial as ext3 fragmentation is a well known issue; [https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf](https://ols2006.108.redhat.com/2007/Reprints/sato-Reprint.pdf) 
I showed filefrag clearly listing the minimum possible number of "pidgeonholes" for my files as 3 in test 1, but the files were severely more fragmented than that. Filefrag takes into account the file size when telling you what is the minimum fragmentation possible. My point wasn't that it wasn't exactly 1 extent - I'm fully aware that 1 extent is not possible if the file size exceeds the max extent size. My point was that ext3 wasn't even close to the perfection value of 3, the fragmentation was significantly affecting performance on a real machine, and there was really nothing simple I could do about it since ext3 doesn't have a production defrag utility. However if a defragmentable filesystem like XFS is used the perfection value can indeed be achieved. Also see test 2 where multiple streams the system writes more extents than necessary even when there's plenty of space left and there's negligible existing fragmentation. I feel like I'm repeating my last post. Show me real results with my exact tests from my previous post run on your 1+ year old ext3 partition with comparable utilization that writes the perfection count of extents. I never said anything about NTFS - saying that ext3 is better than NTFS at preventing fragmentation is not the same thing as defrag not being necessary. Your copy & rewrite thought experiment is quite frankly irrelevant to what I'm talking about. Actually do the tests I described and read the filefrag manual.

---

### Post by Ravernomina on 2009-02-21
Whats the code to check on how much ur drive is fragmented :o

---

### Post by lykwydchykyn on 2009-02-21
Here's looking forward to ext4; salud!


[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by randalph on 2009-02-22
> **Ravernomina said:**
> Whats the code to check on how much ur drive is fragmented :o

Hey I don't know of a great way to measure this. fsck counts all the zero-byte special files as not-fragmented, which makes it look not as fragmented as it is. also I don't think it accounts for the relative number of extra unnecessary extents vs. perfection; just whether it's fragmented or not. "xfs_db -c frag -r <drive>" spits out a number if you're running XFS.. In any case I think spot-checks with filefrag on newly created files like w/ my tests above are actually a more accurate picture than aggregating fragmentation statistics over the entire drive since new files are disproportionately the focus of user-interactive attention. cheers.

---

