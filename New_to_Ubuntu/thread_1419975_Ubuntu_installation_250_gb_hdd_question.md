---
title: "Ubuntu installation 250 gb hdd question"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by aloprot on 2010-03-02
I hope I will not bother anyone but I came across a funny problem. I installed ubuntu 9.10 on a brand new 250 hdd and I went on my home folder to check how much space I have. And surprise, I have only 205 gb. HUh? I don't think ubuntu ocupies 40 gb space and I have nothing installed or other files such as media files..games and things like that only Ubuntu. Why 40 gb are gone? THis is a 250 gb drive on a 64 bit 9.10 ubuntu.

---

### Post by Arijit_Kundu on 2010-03-02
"250 GB" hard drive = 250,000,000,000 bytes / 2^30 bytes in a gigabyte = 232.83 GB

but 205 gb is too small. can you run 
sudo fdisk -l

in the terminal (under accessories in the menu), and post the output?

---

### Post by Cabs21 on 2010-03-02
that is how much room your home folder has as free space but this is in no way your full system free space.  If you want to know your system free space I suggest checking the properties of the folder called filesystem or better yet use gParted to see what your HDD data usage looks like.

---

### Post by aloprot on 2010-03-02
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac45278c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

---

### Post by Arijit_Kundu on 2010-03-02
can you see that there are 3 partitions?, that is why you have 205 gb in home.

To check individual partition sizes in more human readble way, 
go to system > administration > system monitor
there in the File system menu, you'll see the sizes.

---

### Post by Arijit_Kundu on 2010-03-02
And, I think you have put rather a large space in the / directory.
;)

---

### Post by aloprot on 2010-03-02
I have checked system monitor and I have /dev/sda1/ -ext4- which has a total of 219,9 gib, free 216,5 available 205,3 and used 3,4. Is this ok? I'm still a little confuse why I there it says 205,3 gib available. 250 minus 3,4 doesn't give me only 205,3 gib to use.
And by the way I putted nothing nowere, I erased the disk entirely and let ubuntu partition it by the way he wanted.

---

### Post by Arijit_Kundu on 2010-03-02
well well, see above my first reply to your question, a 250gb hdd does not actually mean 250gb!

---

### Post by halitech on 2010-03-02
open a terminal and run

```
df -h
```

then use the quote tags to post the info here

---

### Post by aloprot on 2010-03-02
/ 2^30 bytes in a gigabyte = 232.83 GB

but 205 gb is too small


I get available space 205,3 in system monitor.  And a total of 219,9 gib which is not equal with your 232.83 gib. Sorry is just that it's confusing. I don't understand why I have there free space 216,5 gib  but available only 205,3 gib. And why if you have a 250 hdd you can't use 250 gb? Why is it then a 250 gb then? Sorry, I don't mean to be rude or something is just that I don't understand.

By the way thank you for your help.

---

### Post by halitech on 2010-03-02
> **aloprot said:**
> / 2^30 bytes in a gigabyte = 232.83 GB

but 205 gb is too small


I get available space 205,3 in system monitor.  And a total of 219,9 gib which is not equal with your 232.83 gib. Sorry is just that it's confusing. I don't understand why I have there free space 216,5 gib  but available only 205,3 gib. And why if you have a 250 hdd you can't use 250 gb? Why is it then a 250 gb then? Sorry, I don't mean to be rude or something is just that I don't understand.

By the way thank you for your help.

hard drive makers round things off and use 1000 instead of the actual 1024 which is an actual meg. Sounds better to say a drive is 250gig then saying its 232gig

---

### Post by Arijit_Kundu on 2010-03-02
but what about the other two partitions (sda2 and sda5)?

---

### Post by Cabs21 on 2010-03-02
read this thread.  similar problem with an answer that might help.

[http://ubuntuforums.org/showthread.php?t=1391699](http://ubuntuforums.org/showthread.php?t=1391699)

---

### Post by achase79 on 2010-03-02
an extended and a logical partition.  One is contained within the other, they act as one.

---

### Post by aloprot on 2010-03-02
In system monitor at file systems I have two things.
/dev/sr0 which is my DVD. It's an ubuntu dvd in my laptop.

/dev/sda1/ which is a ext4-Total219.9gib-free space 216.5 gib-available space 205.3 gib-used 3.4 gib(1%). This is all I got in file systems.

---

### Post by Paddy Landau on 2010-03-02
> **aloprot said:**
> I have checked system monitor and I have /dev/sda1/ -ext4- which has a total of 219,9 gib, free 216,5 available 205,3 and used 3,4. Is this ok? I'm still a little confuse why I there it says 205,3 gib available. 250 minus 3,4 doesn't give me only 205,3 gib to use.
Part of the disk is the swap partition (that's the sda2 & sda5 that you posted earlier).

The other part of the disk is sda1, and it contains not only Ubuntu but also the index, which Linux uses to keep track of what's on the disk. The index can be quite large.

If you can run gparted (System > Partition Editor or GParted), and post a screen-shot, we can probably give you a better answer.

---

### Post by Cabs21 on 2010-03-02
get gParted and read this thread

[http://ubuntuforums.org/showthread.php?t=1391699](http://ubuntuforums.org/showthread.php?t=1391699)

---

### Post by aloprot on 2010-03-02
Are you talking about system>administrator>palimpsest disk utility? I have no gparted
Ohh and my laptop came with ubuntu 9.04 preinstalled. I erased it and installe 9.10 because of some problems when updating to 9.10. Don't know if this helps.

---

### Post by halitech on 2010-03-02
do it the easy way, open a terminal and run
```
df -h
```
then you can copy and paste the info back here for us to look at and hopefully explain where your space is being used

---

### Post by aloprot on 2010-03-02
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G  3.5G  206G   2% /
udev                  2.0G  304K  2.0G   1% /dev
none                  2.0G  8.9M  2.0G   1% /dev/shm
none                  2.0G   92K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sr0              691M  691M     0 100% /media/cdrom0

---

### Post by aloprot on 2010-03-02
Did I did that correctly? Do you need other info?

---

### Post by anaconda on 2010-03-02
wonder why no-one mentioned that ubuntu unnecessarily reserves  5% of hd space for root user

it can be adjusted with 
sudo tune2fs -m 1 /dev/sda1
(to change the value to 1%...)

The 5% space is reserved for root, so that if/when the disk gets full, then root still can boot to recovery mode, and has enough room to move around, and free some space. All fine, and good, but... the 5% was a good procentage when hd-sizes were ~2Gb or so... It hasn't been changed since..) It is totally nuts on a 250GB hd. One procent would be more than enough AND even that is only needed on the root partition.. not in home partition.
(and even then a liveCD can do the same job.. ie. free space from hd if it gets full..)

You can search the forums for more info of the tune2fs..

---

### Post by aloprot on 2010-03-02
Thanks, didn't knew that but I'm still confused where all my space is going and how to find out what spaces does everything take from my hdd including root.

---

### Post by halitech on 2010-03-02
> **aloprot said:**
> 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G  3.5G  206G   2% /
udev                  2.0G  304K  2.0G   1% /dev
none                  2.0G  8.9M  2.0G   1% /dev/shm
none                  2.0G   92K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sr0              691M  691M     0 100% /media/cdrom0
```


that is showing 3.5gig used but where is the info for /dev/sda2 ? it should be showing all the partitions unless you have  unpartitioned space on the drive

here is mine
```

daryl@debian:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              28G  6.3G   20G  24% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
udev                   10M  328K  9.7M   4% /dev
tmpfs                1007M  224K 1007M   1% /dev/shm
/dev/sda2             118G   52G   60G  47% /home
/dev/sdb2             289G  148G  127G  54% /home/daryl/storage
/dev/sdc1             184G   66G  110G  38% /home/daryl/storage2
/dev/sdb1             5.2G   29M  5.1G   1% /media/ntfs

```

---

### Post by aloprot on 2010-03-02
There doesn't seem to be a sda2/ What can I do?

---

### Post by halitech on 2010-03-02
now I would say you will need partition editor to find out about the missing /sda2

---

### Post by teward on 2010-03-02
I asked the guy over IRC to provide a screenshot of gparted (yes, I use gparted so I can see the partitions visually, and I like gparted over terminal commands :P).

I'll put the link to his screenshot here.

Then I'll mark it up explain it to him a bit, so perhaps he can visually understand it.


***EDIT: Linkage to his original screenshot: [http://img9.imageshack.us/i/screenshotej.png/](http://img9.imageshack.us/i/screenshotej.png/) ***

---

### Post by Paddy Landau on 2010-03-02
Thanks for the screenshot.

Here's what I see.

[LIST]
[*]sda1: This is your Linux installation, both root and home. It has 223.41Gb, of which 6.93Gb is used, leaving 216.47Gb available. (I guess it doesn't add up due to rounding errors.)
[*]sda2: This is an extended partition, which simply means a partition that holds other partitions. (Extended partitions exist because, for historical reasons, a drive can have only four partitions; extended partitions allow drives to have more than four.)
[*]sda5: This fills sda2 completely, and is your Linux swap partition. (Unlike Windows, Linux uses a separate swap partition instead of a big file in the main area.) The swap is enormous at 9.48Gb; if you have 1Gb or more of RAM, it need be only as large as your RAM.
[/LIST]
I hope that answers your questions, and that you feel more comfortable now.

By the way, I believe that GParted uses GiB, which means 1,024 bytes per Kb, or 1,073,741,824 bytes per Gb.

---

### Post by teward on 2010-03-02
Marked up version with my details and some notes is here:

[http://img691.imageshack.us/img691/69/screenshotejmarkedup.png](http://img691.imageshack.us/img691/69/screenshotejmarkedup.png)



Hope this helps.

---

### Post by aloprot on 2010-03-02
TrekCaptainUSA, thank you. It helped a lot. Thanks so very much!

---

