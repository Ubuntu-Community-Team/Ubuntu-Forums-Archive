---
title: "Slow copying to jfs filesystem"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by scweston on 2009-05-03
Hi all,

I've recently done a fresh install of Jaunty and added mythtv to the installation.

I have partictioned my single physical drive as such: -
/dev/sda1   Ext3  /         23.28GB
/dev/sda2   swap            1.86GB
/dev/sda3   Ext3  /home     93.14GB
/dev/sda4   JFS   /mystuff  347.48GB

I tend to save most of my stuff to the /mystuff partition which is JFS. I use it for mythtv recordings, saving movies, music and even where I store the virtualdrive I use for windows xp in VirtualBox (also installed). As you can imagine it has a lot of large files on it.

The problem is if I'm copying to the JFS filesystem it is really slow (around 2.7MB/sec). On the other hand if I copy the other way around (i.e. to an ext3 partition from the JFS partition) it is really quick (around 31.5MB/sec). The problem appears more noticeable on larger files.

The reason I'm concerned is that I've never noticed this when I had hardy installed (I skipped intrepid) and also could this be a problem if i'm doing multiple recordings in mythtv.

Any ideas on how to fix this slow copy rate. Your help is much appreciated.

Stephen

---

### Post by MontelEdwards on 2009-05-03
JFS is the oldest filesystem for Linux i believe.
Why didnt you just do EXT4?

---

### Post by rhcm123 on 2009-05-03
> **scweston said:**
> 
Any ideas on how to fix this slow copy rate. Your help is much appreciated.

Stephen

Try converting to a new filesystem (e.g. ext2/3/4.). I was using jfs for my backup drive (inter-compatibility, and my 1999 file server can't take much strain), and it was so slow i upgraded to ext2 and it copies at 3 times the old rate (and this is over usb 1.1, so it's very noticeable, and the CPU drain is negligible, 2% or so) :D

The only problem i can see is where you will store your data in the meantime... :confused:

EDIT: A quick forum search found me a site that has a script to find out which will work best on your machine:
[http://fsbench.netnation.com/](http://fsbench.netnation.com/)

---

### Post by scweston on 2009-05-03
Thanks for the help!

The reason it's JFS is that when I did my first install of an ubuntu OS a while back I was setting everything up to use as a mythtv system. At the time I'm sure a read on some thread somewhere that JFS was superior to ext3 for mythtv recordings and for storing very large files (is this now wrong?).  Also, to change the filesystem is a hassle as I would need a temporary storage device somewhere to copy everything temporarily (i'm sure I could get hold of a USB drive if necessary).

I'm worried about using ext4 as there have been some posts on this site suggesting that there are data loss issues if there was to be a sudden power failure or computer crash. When these issues are resolved I will perhaps consider ext4.

I will do some more research in to the best filesystem methinks!! Although if anybody could just tell me what would be the safest, most reliable and fastest filesystem for mythtv recordings and general large files (movies etc) please do tell.

Stephen

---

### Post by cariboo on 2009-05-03
I just set up a file server, and I had the same worries about ext4, even though I've been using it for 3 months on my desktop with no problems. As of right now it seems that ext4 is the fastest, but xfs is a close second. what convinced me to go with xfs was this article in [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1"). I created a 10Gb ext3 / partition, and the rest of the partitions are formatted as xfs I get 70-80Mbps transfer rates when copying files back and forth on the network.

---

### Post by rhcm123 on 2009-05-03
> **scweston said:**
> Thanks for the help!

The reason it's JFS is that when I did my first install of an ubuntu OS a while back I was setting everything up to use as a mythtv system. At the time I'm sure a read on some thread somewhere that JFS was superior to ext3 for mythtv recordings and for storing very large files (is this now wrong?).  Also, to change the filesystem is a hassle as I would need a temporary storage device somewhere to copy everything temporarily (i'm sure I could get hold of a USB drive if necessary).

I'm worried about using ext4 as there have been some posts on this site suggesting that there are data loss issues if there was to be a sudden power failure or computer crash. When these issues are resolved I will perhaps consider ext4.

I will do some more research in to the best filesystem methinks!! Although if anybody could just tell me what would be the safest, most reliable and fastest filesystem for mythtv recordings and general large files (movies etc) please do tell.

Stephen

JFS actually supports the largest file size of all modern file systems: 4 petabytes (although if you have a 4 petabyte file, you've got a bigger problem :) ), as opposed to ext4, which supports ~16 TB. JFS is also the least processor-intensive filing system, which makes it a plus for older boxes (why I chose it for my backup drive, before switching to ext2).

I have personally heard that ext4 is better than ext3 (which will be permanently corrupted if anything happens to the journal) on power failures, but I have yet to personally try it (I'm still on 8.10 here on my lappy). However, ext4 is still in the working-the-kinks-out phase, so perhaps ext2/3, XFS, or ReiserFS is better.

I would personally reccomend you XFS, as it is one of the oldest filing systems available (I think the first version was 1994, 1996???, it came out sometime near JFS). If this is not the main file system (that is, / ), then go for it (GRUB and XFS don't agree with each other).

But continue reading - I didn't know XFS and GRUB didn't work together until a Google search!

---

### Post by Stupendoussteve on 2009-05-04
XFS and Grub work fine in Ubuntu (at least Jaunty). XFS can mangle your data in a power failure though, just like ext4 did but doesn't now.

JFS does not suffer this problem, but is slower than XFS/ext4. (A note on ext2, this is of course very fast, it doesn't have any sort of journal)

JFS is largely unmaintained. It gets poked here and there by the maintainers, but they generally work on other projects.

---

### Post by rhcm123 on 2009-05-04
> **Stupendoussteve said:**
> XFS and Grub work fine in Ubuntu 
Thats at least true for ubuntu, but redhat/fedora have some issues: [https://bugzilla.redhat.com/show_bug.cgi?id=250843](https://bugzilla.redhat.com/show_bug.cgi?id=250843)

---

### Post by scweston on 2009-05-04
Thanks everyone for suggestions!

Following some of the advice on this thread I think I'm going to reformat the partition to xfs. It sounds like this is both fast and reliable. If anyone would like to suggest why this wouldn't be a good idea then please do tell me before I take the plunge.

I've decided not to use ext4 until its been through 'working-out-the-kinks phase' a bit more.

Before I do start on reformatting can I just check that all I need to to is backup the data on the partition to another drive, reformat the partition to xfs (using something like gparted), restart the system then copy all the data back to the drive?   Is it safer to do this kind of surgery using a live cd? Do I need to make any changes to any configuration files (such as fstab), etc?

Again, any help is appreciated!

Stephen

---

### Post by rhcm123 on 2009-05-06
> **scweston said:**
> Thanks everyone for suggestions!

Following some of the advice on this thread I think I'm going to reformat the partition to xfs. It sounds like this is both fast and reliable. If anyone would like to suggest why this wouldn't be a good idea then please do tell me before I take the plunge.

I've decided not to use ext4 until its been through 'working-out-the-kinks phase' a bit more.

Before I do start on reformatting can I just check that all I need to to is backup the data on the partition to another drive, reformat the partition to xfs (using something like gparted), restart the system then copy all the data back to the drive?   Is it safer to do this kind of surgery using a live cd? Do I need to make any changes to any configuration files (such as fstab), etc?

Again, any help is appreciated!

Stephen

Sorry about the late response, the email wasn't sent apparently. Now...

FIRST THING: BACKUP, BACKUP, BACKUP!!!

You don't need to use the live cd to use this, but of course you can. I would use your default install to make it faster. Simply unmount your drive (you said it was at /mystuff), then you can begin.
Grab gparted (not included on desktop installs), and xfsutlis (that's probably not right, but you get the idea), because you will need that to make and mount the partition. Now, do the making (BE SURE TO ONLY USE THE PARTITON YOU UNMOUNTED, FORMATTED JFS!!!) in gparted, and keep in mind that xfs partitons cannot be resized after creation. After you get your drive the way you would like it (and you don't break it :D), then write it to disk.

After that, edit the fstab, so that it goes from this: (EXAMPLE!)
```

# /dev/sda2 - DATA PARTITION
UUID=af5e4c88-a797-478d-b55b-851560b55daf /mystuff               **jfs**    defaults 0       0
```
To:
```

# /dev/sda2 - DATA PARTITION
UUID=af5e4c88-a797-478d-b55b-851560b55daf /mystuff               **xfs**    defaults 0       0
```

After that, run this command:
```
sudo mount /mystuff
```
to mount the partition

---

### Post by scweston on 2009-05-06
Thankyou rhcm123,

I haven't yet done the work. Will probably get around to it this weekend, but your post i'm sure will certainly help!

I let you know if I have any problems.

Stephen

---

### Post by rhcm123 on 2009-05-27
> **scweston said:**
> Thankyou rhcm123,

I haven't yet done the work. Will probably get around to it this weekend, but your post i'm sure will certainly help!

I let you know if I have any problems.

Stephen

one last thing about xfs and disklabels. I just reformatted my external hdd for my lappy XFS. We had a power failure here, and while my lappy (duh) was fine, the USB drive was not, so I took the oppourtuity to reformat. However, Gparted didn't make my label (PORTABLE - self explanatory :D) and I wanted to fix that.

====IF YOU HAVE YET TO FORMAT====
If you want to use a label, then you need to create a blank partition in gparted, NOT an xfs partition. Then run this command in terminal:
```
sudo mkfs.xfs -f -L <label> /dev/<drive> 
```
The problem is that gparted puts the <label> in quotes, which xfs doesn't like.

====IF YOU HAVE FORMATTED====
Do the following: (this assumes the drive is umounted)

Grab the XFS admin programs (which you need anyways for gparted to work):
1. sudo apt-get install xfsprogs

Apply the label:
2. sudo xfs_admin -L <label> /dev/<drive>

---

### Post by scweston on 2009-05-31
Thankyou rhcm123,

I haven't yet managed to get around to doing the job. I hope to soon, but other things have cropped up recently which have taken priority. Although I really do appreciate your continued information/support. It will certainly help when I finally do get around to this.

Stephen

---

