---
title: "How Do I Create a Partition for /home?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by alohatim on 2009-02-09
I want to create a partition and put my home folder on it.  I want to share it with Windows XP.  I installed the FS thing in XP and was hoping to at least read my current ext3 partion.  The error message I got was "The file system has an inode size unequal to 128 bytes (inode size: 256 bytes). The only way to solve it is to backup the volume's files and format the file system: give the mkfs.ext3 utility the -I 128 switch."  Huh??!?

I booted with the gparted disk.  I was hoping I could create a partition and then figure out how to format it with that mkfs thing.  Gparted says I cannot create any new partitions.  This is my fdisk -l:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        2610    20932695    7  HPFS/NTFS
/dev/sda3            2611        7297    37648327+   5  Extended
/dev/sda5            2611        7205    36909306   83  Linux
/dev/sda6            7206        7297      738958+  82  Linux swap / Solaris

I don't know what to do now.  I'd like to shrink sda5 down to 10 gigs and stick a 25 gig partition in for data.  I thought that these were extended partitions and I could make as many as I wanted.  Why does gparted say that I cannot make any more?

Once I make the partion, how do I make sure that windows can see it? 

If I need to, I can wipe out everything and start over--but I think that I am fairly close to getting this right.   

Thanks and aloha!

---

### Post by Paqman on 2009-02-09
> **alohatim said:**
> I thought that these were extended partitions and I could make as many as I wanted.  Why does gparted say that I cannot make any more?


Probably because Gparted can't change any partition that is in use. Since your root partition is within the extended, you can't modify any part of the extended.

Simple solution though: boot into your LiveCD, it has Gparted on it already. Since your swap is also inside your extended (and the LiveCD automatically mounts any swaps it sees) right click on your swap in Gparted and select "swapoff". That'll free up your extended partition so you can make changes.

There's some good instructions on Psychocats about [URL="http://www.psychocats.net/ubuntu/separatehome"]creating a separate home
[/URL].

---

### Post by alohatim on 2009-02-09
Thanks, Paqman.  Even when I boot with a gparted cd, the partitions are in use?  I didn't really see any partitioning tools in the intalled version of Intrepid, so I assumed it wasn't on the live cd.  I will try it now.  

Thanks, again!

---

### Post by alohatim on 2009-02-09
I rebooted with the live cd and started gparted.  I did swapoff on the swap file.  

It seems to act the same way it did when I booted from the gparted cd.  Partition/New is grayed out.  I can click Resize/Move on the sda5 partition but when the window opens, I can't change the New Size and the Resize/Move button is grayed.  

What do you think?

---

### Post by 2hot6ft2 on 2009-02-09
Once you get the partitions set up here is the guide I used to move home on both of my installs, it's a little newer than some of the others as well as being real simple.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Paqman on 2009-02-09
> **alohatim said:**
> 
What do you think?

Do any of the partitions have a little key symbol on them in Gparted? If so, those ones are mounted, and you'll want to unmount them.

---

### Post by alohatim on 2009-02-10
Paqman: I don't see any symbols next to them.  If I right-click on any partition, the unmount option is grayed. 

2Hot: That looks great.  I will try those instructions.  I tried Pschocat's last time and screwed it up.  Something got messed up with permissions.  I reinstalled and started over.  Thanks for the tip.

---

### Post by unutbu on 2009-02-10
From [http://ubuntuforums.org/showpost.php?p=6167548&postcount=9:](http://ubuntuforums.org/showpost.php?p=6167548&postcount=9:)
> Intrepid by default formats its ext3 partitions to use the newer 256 byte inode size for its file system, whereas Hardy and previous versions use the older 128 byte inode size ext3 partitions. The Grub that comes in versions prior to Hardy can't handle the newer 256 byte inode size partitions.

This is probably why the Windows fs-driver could not read your Intrepid ext3 partition.

Perhaps -- this is speculation, I don't know this for sure --  older versions of GParted also have a problem reading newer ext3 filesystems with 256 byte inode size. 

The GParted that comes with the Intrepid LiveCD should work. If you are using a Hardy LiveCD, perhaps try an Intrepid LiveCD.

---

### Post by alohatim on 2009-02-10
Thanks, Unutbu.  Useful information.  I had used the Intrepid live CD.  I can still format the partition to 128 inode, right?  That is assuming I can make a partition.

---

### Post by unutbu on 2009-02-10
Indeed. Once you create a new partition, say, /dev/sda7, then you could format it with
```

sudo mkfs.ext3 -I 128 -m 0 /dev/sda7
```
Since sda7 would be a data partition, there is no need for reserved blocks. "-m 0" sets the reserved-blocks percentage to 0. The default is 5%. On a 25GB partition this will save you 1.25GB.

I'm stumped as to why GParted is not allowing you to resize sda5 while booted from the LiveCD. 

I have to go now, but perhaps if you boot the LiveCD,
open a terminal and type
```

mount
gksu gparted
```
This will help us debug this situation.
The mount command will make it crystal clear if sda5 is mounted.
By launching gparted from the command line, you will see if there are any error messages. 

Please post the output and I (tomorrow) or others (hopefully sooner) will take a look.

---

### Post by alohatim on 2009-02-10
Aha.. I think I did it.  I rebooted with my gparted cd.  My problem was that I kept trying to modify the size of the existing partition.  When I tried to modify the Space Before, it automatically resized the other part.  Then I was able to make that unallocated space a new partition.  

So next thing I guess is to use mkfs to change the inode size.

---

### Post by alohatim on 2009-02-10
Beautiful!  The new partition exists and I was able to format it with mkfs.  Later, I will attempt to put my /home folder there.

---

### Post by alohatim on 2009-02-10
My new partition is sda7.  I did blkid but it doesn't show sda7.  I wonder why.

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D2-0C05" TYPE="vfat" 
/dev/sda2: UUID="C228AC5828AC4CEB" TYPE="ntfs" 
/dev/sda5: UUID="eecfffcd-4c5a-4412-b631-74ada5120b4c" TYPE="ext3" 
/dev/sda6: UUID="c3eecd48-bbba-45eb-bd12-ddf218112487" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

I remember looking at properties of the partition some other way that I cannot remember now.  I was able to see the UUID from that.

---

### Post by unutbu on 2009-02-10
Sometimes when you have just made a new partition, the computer's cachefile, /etc/blkid.tab, is not updated yet and so the UUID does not show up in the output of blkid.

In that case, use:
```
sudo vol_id /dev/sda7
```

---

### Post by alohatim on 2009-02-11
Thanks, Unutbu.  It is still not showing after several reboots in the blkid list.  sudo vol-id shows it fine.

I edited the fstab like described in PartioningHomeMoving article.  This is the line I added: 
UUID=10808219-9d64-4b83-8619-142441f9a606   /media/home    ext3          nodev,nosuid       0       2

When I try to mount, I get "mount point /media/home does not exist"

I am not sure what to do here.  Thanks for your continued help!

---

### Post by unutbu on 2009-02-11
Run the command
```

sudo mkdir /mount/home

```
This will create the /mount/home directory, so you won't get the
error "mount point /media/home does not exist" any more.

---

### Post by alohatim on 2009-02-11
Thanks, unutbu!  I think you meant mkdir /media/home, right?  I did that and it worked.  

Thanks for all your help!  I everything is perfect now.

---

