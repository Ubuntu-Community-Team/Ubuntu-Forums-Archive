---
title: "fdisk, mkfs. help"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by apgrnt on 2010-06-11
I got a terabyte external as a birthday gift. It's pretty cool.

It came with some software on it for, windows stuff. Well i hate this **** so i just tried to format my hdd. success. I used 
sudo mkfs -t ext3 /dev/sdc
to do my buisness.
then i used 
fdisk to make a primary partition.

Then i ran into a problem, two.
one i can't actually put anything on the disk, and it won't seem to mount.
two, and i think this is minor, it does show the disk is there as a 930 gig hdd. (but fdisk -l reads it as 1000 gigs)
any help?

---

### Post by tarps87 on 2010-06-11
You may want to try formating the partition you created :) (sudo mkfs -t ext3 /dev/sdc1 *probably*) You could always use gparted if you wanted a GUI

---

### Post by Drenriza on 2010-06-11
What i do is that i use a live boot cd 
Hirens Boot Cd

To create my primary, extended, secondary, swap partitions.
I think it works the best.

---

### Post by srs5694 on 2010-06-11
To clarify some of the above: You did it backwards. You should partition the disk *first* (using fdisk, gdisk, GNU Parted, GParted, or other tools), then create the filesystem(s) *second* (using mkfs, GNU Parted, GParted, or other tools). The libparted-based tools (GNU Parted, GParted, and others) enable you to do both things at once, or at least using a single command.

By creating a filesystem on the disk as a whole (/dev/sdc) and then creating partitions on the disk, you've effectively wiped out the filesystem. (It's actually still there, but it's inaccessible.) You should create a new filesystem on the *partition* (probably /dev/sdc1) to use it.

The 930GB/1000GB issue is probably one of the definition of "GB." Disk manufacturers define "GB" as "10^9 bytes," but most disk utilities define "GB" as "2^30 bytes" -- a value that's really a gibibyte (GiB). 1,000 GB = 931 GiB. Post the exact output of "fdisk -lu" if you want a specific analysis of your disk on this score -- but a little arithmetic should help you figure it out. See also [the Wikipedia article on "gigabyte"](http://en.wikipedia.org/wiki/Gigabyte) for more information. Note that similar differences apply to kilobyte, megabyte, terabyte, and other measures.

---

### Post by -kg- on 2010-06-11
What srs5694 said is essentially correct.  The "mkfs" command formats an existing partition.  With your commands, it formatted your existing partition as ext3.  When you then created a primary partition using fdisk, you deleted that partition and created another, formatted (or not) depending on what parameters you passed to it.  If you haven't, you should read the man pages on "fdisk".  There are a few other "versions" of it that do different things different ways.

In any case, I always advocate using GPartEd for partitioning operations.  It is available on the Ubuntu Live CD, or on it's own Live CD, download-able [from here]("http://gparted.sourceforge.net/download.php").  This partition editor does all that fdisk or mkfs does (as matter of fact, it uses these commands as it's front end) with a GUI and adds a few "protections" against making partitioning errors.

You can accomplish what you want to do in two ways.  You can format the existing partition, as srs5694 said, or you can delete that partition and recreate it.  Either way is good, but you should know both options, just in case.

A good guide to partitioning operations can be found at the link in my signature block.  This method primarily deals with GPartEd.

---

### Post by srs5694 on 2010-06-11
> **-kg- said:**
> What srs5694 said is essentially correct.  The "mkfs" command formats an existing partition.  With your commands, it formatted your existing partition as ext3.

Not quite. The specified command was:

```

sudo mkfs -t ext3 /dev/sdc

```

This command creates an ext3 filesystem on /dev/sdc -- that is, on the entire disk, which is then unpartitioned. This is legal, but a bit strange. Normally you see this sort of thing only on floppies and some removable disks. Most disks, even most removable disks, are partitioned for use, even if to create just one partition.

> When you then created a primary partition using fdisk, you deleted that partition and created another, formatted (or not) depending on what parameters you passed to it.

The standard Linux fdisk utility, part of util-linux-ng, does not create filesystems; it *only* manipulates the partition table.

BTW, the term "format" is extremely vague. It's most often used as a synonym for "creating a filesystem," as you seem to be using it; but some people use it to refer to partitioning, low-level formatting (possible with floppies but not normally possible with hard disks), or sometimes other operations.

> In any case, I always advocate using GPartEd for partitioning operations.  It is available on the Ubuntu Live CD, or on it's own Live CD, download-able [from here]("http://gparted.sourceforge.net/download.php").  This partition editor does all that fdisk or mkfs does (as matter of fact, it uses these commands as it's front end) with a GUI and adds a few "protections" against making partitioning errors.

The [GNOME Partition Editor (aka GParted)](http://gparted.sourceforge.net/) is based on the [GNU libparted](http://www.gnu.org/software/parted/index.shtml) library, which also provides the GNU Parted (aka parted) text-mode tool. I'm 99.9% sure that none of these tools uses fdisk as a front-end (although there is a libparted-based GNU fdisk, which is distinct from the standard Linux fdisk). I'm not sure precisely how they do their filesystem creation tasks; they might use mkfs or link to the same libraries that mkfs (or its helper applications) use.

Although both fdisk and libparted-based tools work in much the same way for many purposes, there are things that one or the other does better. Since most libparted-based tools can create filesystems when they create partitions, they can be more convenient, particularly for new users. These tools can also handle more partition types (MBR, APM, GPT, and others), and they can move and resize partitions and the filesystems they contain. These are all important benefits. OTOH, libparted tends to flake out when presented with disks that have certain types of minor errors; fdisk handles such problems better. Linux fdisk also enables changing partition type codes and making other low-level changes that are difficult or impossible with libparted-based tools. Similarly, libparted-based tools provide a convenient and user-friendly interface for filesystem creation; but they omit more advanced options that are accessible via mkfs or its helper programs (mke2fs, mkreiserfs, etc.).

---

### Post by apgrnt on 2010-06-11
I've got a partition set up under /dev/sdc1, should be the entire hdd. then i formatted that with the command: sudo mkfs -t ext3 /dev/sdc1

so i should have a working external hdd now, i'd think. I can mount the disk and look at it. but thats it. there is a folder in there called "lost + found" that i can't open and i can't add files to the folder. 
i'll try gparted and see if i have any luck there. but there is something i'm not doing right in the console.

---

### Post by srs5694 on 2010-06-11
Your problem now is one of permissions. Type the following at a text-mode command prompt:

```

sudo chown yourusername: /mount/point

```

Change "yourusername" to your username in Ubuntu, and change "/mount/point" to wherever the partition is currently mounted.

---

### Post by -kg- on 2010-06-12
> **srs5694 said:**
> Not quite. The specified command was:

```

sudo mkfs -t ext3 /dev/sdc

```

This command creates an ext3 filesystem on /dev/sdc -- that is, on the entire disk, which is then unpartitioned. This is legal, but a bit strange. Normally you see this sort of thing only on floppies and some removable disks. Most disks, even most removable disks, are partitioned for use, even if to create just one partition.

Yes, I can see your point.  I misread that portion of the command, and recognize that it would format the entire device without "creating" a partition on it.  But I can find no information on what the command would do if a partition already existed on the device.  Since the command has nothing to do with the partition table as such, would it not "create the file system," if you will, formatting the existing partition without destroying it?

I may have to do a little experimentation with that.  I have a "spare" hard drive (the one I used in "How To Partition" to create the screenshots) and see what the command would do in this case.

> **srs5694 said:**
> The standard Linux fdisk utility, part of util-linux-ng, does not create filesystems; it *only* manipulates the partition table.

From [this Ubuntu Community Man Page]("http://manpages.ubuntu.com/manpages/jaunty/man8/fdisk.8.html"):

> fdisk is a disk partition manipulation program, which allows you to [COLOR="Red"]create, destroy, resize, move and copy partitions[/COLOR] on a hard drive using a menu-driven interface.

I find a general consensus on this from other sources, as well.

> **srs5694 said:**
> BTW, the term "format" is extremely vague. It's most often used as a synonym for "creating a filesystem," as you seem to be using it; but some people use it to refer to partitioning, low-level formatting (possible with floppies but not normally possible with hard disks), or sometimes other operations.

These days, formatting is normally used for "creating a file system" as opposed to "low-level formatting", considering that floppies and other such small media are everything but ancient history.  Even in GPartEd, the operation to create a file system in a partition is under the menu, "Format To."

> **srs5694 said:**
> The [GNOME Partition Editor (aka GParted)](http://gparted.sourceforge.net/) is based on the [GNU libparted](http://www.gnu.org/software/parted/index.shtml) library, which also provides the GNU Parted (aka parted) text-mode tool. I'm 99.9% sure that none of these tools uses fdisk as a front-end (although there is a libparted-based GNU fdisk, which is distinct from the standard Linux fdisk). I'm not sure precisely how they do their filesystem creation tasks; they might use mkfs or link to the same libraries that mkfs (or its helper applications) use.

You are correct here, and I stand partially corrected.  Under Parted, there is a command called "mkfs".  Whether this actually uses the "mkfs" standalone command, I don't know.  I'm also not actually sure whether the command, "mkpart" uses fdisk to create the partition itself.

> **srs5694 said:**
> Although both fdisk and libparted-based tools work in much the same way for many purposes, there are things that one or the other does better. Since most libparted-based tools can create filesystems when they create partitions, they can be more convenient, particularly for new users. These tools can also handle more partition types (MBR, APM, GPT, and others), and they can move and resize partitions and the filesystems they contain. These are all important benefits. OTOH, libparted tends to flake out when presented with disks that have certain types of minor errors; fdisk handles such problems better. Linux fdisk also enables changing partition type codes and making other low-level changes that are difficult or impossible with libparted-based tools. Similarly, libparted-based tools provide a convenient and user-friendly interface for filesystem creation; but they omit more advanced options that are accessible via mkfs or its helper programs (mke2fs, mkreiserfs, etc.).

Again, I agree.  This is why I usually suggest GPartEd or another GUI-based partition editor for newer or less experienced computer users.  In general, these tools will enable the less experienced user to do most partitioning operations with ease, and with less chance for accidents.  Someone who becomes experienced enough to do "changing partition type codes and making other low-level changes that are difficult or impossible with libparted-based tools" will learn to use the more powerful tools, or look up the information on their own.

This is why I (re)wrote the documentation linked to in my signature block (kg5uc is my screen name there).  It's a basic guide for partitioning for the "newbie" who just wants to do some basic partitioning operations without having to rely on (very often) complicated and rather dangerous usage of command line commands and software.

---

### Post by srs5694 on 2010-06-12
> **-kg- said:**
> Yes, I can see your point.  I misread that portion of the command, and recognize that it would format the entire device without "creating" a partition on it.  But I can find no information on what the command would do if a partition already existed on the device.  Since the command has nothing to do with the partition table as such, would it not "create the file system," if you will, formatting the existing partition without destroying it?

No, because you're telling it to create the filesystem on the entire disk -- that is, to use sectors 0-{end}, vs. on the existing partition, which is sectors {positive_value}-{something_less_than_end}.

> **-kg- said:**
> [quote=srs5694]The standard Linux fdisk utility, part of util-linux-ng, does not create  filesystems; it *only* manipulates the partition table.

From [this Ubuntu Community Man Page]("http://manpages.ubuntu.com/manpages/jaunty/man8/fdisk.8.html"):

> fdisk is a disk partition manipulation program, which allows you to [COLOR=Red]create, destroy, resize, move and copy partitions[/COLOR] on  a hard drive using a menu-driven interface. 

I find a general consensus on this from other sources, as well.[/quote]

It's unclear if you're agreeing or disagreeing with me. Note the important distinction between partitions and filesystems. A partition is simply a collection of contiguous sectors on the hard disk -- say, sectors 63 to 10,000. Partitions are defined in simple data structures that include start and end sectors (or a start sector and a length) and a few other pieces of data, such as a type code. A filesystem is a much more complex set of data structures that enable files to be stored and accessed by name. Filesystems usually reside within partitions (but not always; they can occupy a whole disk or reside within files or other data containers), and partitions usually hold filesystems (but not always; partitions can be empty or can hold swap space or other data structures). It's possible to alter a filesystem without altering the surrounding partition (say, converting an ext2 filesystem into ext3 format), and it's also possible to alter a partition without altering the contained filesystem (say, using fdisk to increase the size of a partition -- to change that 63-10,000 partition to cover the range 63-20,000). In the latter case, when you mount the filesystem, it'll still show up, in utilities like "df", to be of the original size; to take advantage of the extra space, you've got to increase the size of the filesystem, not just the partition. (You'd do this with resize2fs or a similar utility.)

This distinction is murky and unclear to many people because the most popular partition manipulation tool for desktop Linux users, GParted, combines partition and filesystem manipulations into one operation. In GParted, you click a partition and resize it and the program responds by resizing both the partition and its filesystem. The two are different operations, though.

> These days, formatting is normally used for "creating a file system" as opposed to "low-level formatting", considering that floppies and other such small media are everything but ancient history.  Even in GPartEd, the operation to create a file system in a partition is under the menu, "Format To."

True, but there are many posts in this forum where the term "format" is used in an unclear way, usually to refer to partitioning rather than creating a filesystem. People also sometimes ask about how to "format" a disk to "fix" bad sectors -- something that, interpreted literally, is only possible with a low-level format, although it's possible to block access to bad sectors via a filesystem creation operation.

IMHO, the term is so hopelessly confused that it shouldn't be used. I realize that it is used by GParted, but I disagree with that decision by the GParted programmers. Note that, on cursory examination, the term is not used by the text-mode GNU Parted utility, or by the man page for mkfs.

> I'm also not actually sure whether the command, "mkpart" uses fdisk to create the partition itself.

I just performed a simple experiment: I deleted fdisk from a computer, then I used both GParted and the text-mode GNU Parted to manipulate MBR partitions. Both programs managed just fine, so I can say with 100% certainty that neither relies on fdisk, even for MBR disks. Since fdisk can't handle some disk types that libparted can, such as GPT disks, libparted certainly doesn't rely on fdisk for them, either.

---

### Post by SRST Technologies on 2010-06-12
> **apgrnt said:**
> I've got a partition set up under /dev/sdc1, should be the entire hdd. then i formatted that with the command: sudo mkfs -t ext3 /dev/sdc1

so i should have a working external hdd now, i'd think. I can mount the disk and look at it. but thats it. there is a folder in there called "lost + found" that i can't open and i can't add files to the folder. 
i'll try gparted and see if i have any luck there. but there is something i'm not doing right in the console.
Lost and found is an automatically created folder on every partition but swap partitions.  You have nothing left to do, it is ready to use, provided you mounted it with the proper permissions to let yourself actually use it too.

You cannot access Lost and Found for a reason, only the super user can.  There's nothing you need to do with it anyways, it's never used for any normal reason, and if it is used, you have bigger problems than not being allowed to open the folder.

---

### Post by srs5694 on 2010-06-12
> **SRST Technologies said:**
> Lost and found is an automatically created folder on every partition but swap partitions.

The lost+found directory is a feature of ext2fs, ext3fs, ext4fs, and perhaps some other filesystems. It's not present on FAT, NTFS, ReiserFS, or XFS, and I believe not on JFS, either. I'm not sure about Btrfs, offhand.

---

### Post by SRST Technologies on 2010-06-14
> **srs5694 said:**
> The lost+found directory is a feature of ext2fs, ext3fs, ext4fs, and perhaps some other filesystems. It's not present on FAT, NTFS, ReiserFS, or XFS, and I believe not on JFS, either. I'm not sure about Btrfs, offhand.
A thousand pardons, I did not realize it was possible to create an NTFS partition with the command sudo mkfs -t ext3 /dev/sdc1.

---

### Post by srs5694 on 2010-06-14
I was responding to your claim that "lost and found is an automatically created folder on every partition but  swap partitions." You didn't qualify your claim, but you did specify "every partition," and you did mention swap -- and swap space can't be created by mkfs at all, so your sarcastic response seems rather misplaced to me. I was merely trying to provide additional precision on this issue.

---

