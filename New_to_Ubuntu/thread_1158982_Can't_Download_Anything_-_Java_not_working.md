---
title: "Can't Download Anything - Java not working"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Coh3n on 2009-05-14
Hello,

I'm new to ubuntu, so sorry if this sounds stupid.  I'm duel booting, and have Java on Windows.  When I go to download, it says I don't have enough space in the File System.  It doesn't ask me where I want to download the file even though I have it set to ask me every time.  It automatically says I don't have enough space.  It doesn't give me the option to save it somewhere else.

If there is a way I can run Java on ubuntu without having to reinstall it, please let me know!
I also made sure both the Java options were turned on, and it didn't work.  

I don't want to download the file in the File System, that's where all the ubuntu files are.  I have my other hard drive with over 144GB of space, why won't it let me choose to download there?

If anyone has any suggestions that would be awesome.  Thanks!

Coh3n

Another quick question - can I play iTunes in ubuntu using the music I have saved on Windows.  Sorry if it sounds stupid.

---

### Post by kpkeerthi on 2009-05-14
Post the output of:
```
df -h
```

Put this command in Applications -> Accessories -> Terminal

---

### Post by Coh3n on 2009-05-14
Okay, here:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G  3.9M 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G   92K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  152K  1.5G   1% /dev
tmpfs                 1.5G  484K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   12K 1012K   2% /tmp

---

### Post by bacardiandwatermelon on 2009-05-14
By the looks of things you installed ubuntu onto a 2.3G partition and you ran out of space. Alot of people got caught out by not moving the slider when installing and installing ubuntu onto a tiny partition.

---

### Post by Coh3n on 2009-05-14
Okay I understand that, so do I have to reinstall in a larger partition?

---

### Post by bearozo on 2009-05-14
Have u clicked on "places" and seen your other HDD there ? to make sure it is mounted.

---

### Post by Coh3n on 2009-05-14
Yeah, its there.

---

### Post by Coh3n on 2009-05-14
I just want to know what I need to do to download into my main hard drive, and if I can get Java to work without installing it again on ubuntu.  Thanks.

---

### Post by Niniel on 2009-05-14
Java has nothing to do with your problem.
In order to be able to download anything anywhere, you will need more space for Ubuntu.
Depending on your disk layout and the amount of space available, if any, you may just have to extend your Ubuntu partition. I recommend you give Linux 5 - 10 GB.

---

### Post by Marlonsm on 2009-05-14
> **Niniel said:**
> Java has nothing to do with your problem.
In order to be able to download anything anywhere, you will need more space for Ubuntu.
Depending on your disk layout and the amount of space available, if any, you may just have to extend your Ubuntu partition. I recommend you give Linux 5 - 10 GB.

Maybe you'll need some more, I use 30Gb for mine.

---

### Post by Coh3n on 2009-05-14
Okay, how do I extend the partition?

And, do I still have to install Java again? It can't work from Windows?

---

### Post by hyperdude111 on 2009-05-14
Java is NOT the problem, you will need to install on a larger partition to be able to download. I would recommend 10gb minimum, I use 160.

Once you have done this you may still want java for other reasons, the easiest and best way to install ALL codecs, java, flash, mp4, avi, mp3 etc...... Is with this nifty command.

```
sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by hyperdude111 on 2009-05-14
> **Coh3n said:**
> Okay, how do I extend the partition?

And, do I still have to install Java again? It can't work from Windows?

To extend your partition boot from the ubuntu live cd and open the partition manager and move the slider of you windows partition into free space and then increase the ubuntu partition into that space.

Things in windows and ubuntu are very different, if you have java etc installed in windows it will NOT be installed in ubuntu automatically. They run separately.

---

### Post by Coh3n on 2009-05-14
Alright, thanks Hyper, and everyone else for the help.  I'll give it a whirl.

Also, Hyper, thanks for that code :)

---

### Post by Coh3n on 2009-05-14
I booted from the CD but I couldn't find the Partition manager.  Sorry if I'm being really irritating, but I'm really new to this. Lol.

Or how can I make a new partition?

---

### Post by Niniel on 2009-05-14
No problem.
The partitioner can be found in the bar at the top of the screen:
System/Administration/Partition Manager

---

### Post by Coh3n on 2009-05-14
I found it, thanks. But now there's a bunch there.  I reduced my Windows one, but which is the right ubuntu one to extend?

---

### Post by hyperdude111 on 2009-05-14
> **Coh3n said:**
> I found it, thanks. But now there's a bunch there.  I reduced my Windows one, but which is the right ubuntu one to extend?

The ubuntu partition on your current setup will be about 2.3gb in size and with no free space. It will also be formatted to either EXT4 or EXT3

---

### Post by Coh3n on 2009-05-14
Wonderful, it's in the process now.  Thanks.

---

### Post by Niniel on 2009-05-14
According to an earlier post of yours it's

/dev/sda5 2.3G 2.2G 3.9M 100% /

However, sda5 indicates that this is a logical drive in an extended partition. You may need to extend that partition first before you can increase the size of sda5. Windows is probably sda1, so it could be sda2, depending on your disk layout. In any case, it should say "extended" next to that partition (an "extended" partition is something like a container, so before you can increase the size of what's in the container, the container itself needs to grow).

---

### Post by Coh3n on 2009-05-14
Okay thanks, is it suppose to take like an hour to reduce the partition? And, what is there a big chance I will lose data?

---

### Post by hyperdude111 on 2009-05-14
Re-sizing partitions takes a long time be warned. I have never lost any data in partitioning, but have heard of stories of people who had. If in doubt make a back up.

---

### Post by Coh3n on 2009-05-14
Yeah okay, thanks.  I'll post how it goes.  Thanks everyone!

---

### Post by Coh3n on 2009-05-14
Problem - it won't let me expand the /dev/sda5 it says the max size is 2.32 GiB.

---

### Post by hyperdude111 on 2009-05-15
As said earlier (by someone else) You may need to extend the container the ubuntu partition is in before you can extend the ubuntu partition

---

