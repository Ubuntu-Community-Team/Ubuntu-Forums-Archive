---
title: "test"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by J V on 2010-01-27
Edit: To a mod:
This was an accident, I accidentally posted when I wanted to preview, could you rename this topic please? (Seperate home partition howto) Thanks!

By carefully choosing your partitioning when installing Ubuntu, you can speed up your hard drives, and even let you keep your files and settings with a fresh install!

**Definitions**
HD: Hard-drive, the part of the computer that saves your stuff
File-system: A way to save data, Ubuntu uses the ext4 file-system now
Partition: A "Section" on the HD, it has its own file-system, and can contain files and folders
Format: The action of creating partitions
Mount: The action of loading a partition to be used
Primary: A partition directly on the HD, there are a maximum of 4 of these
Extended: A partition that can hold a number of logical partitions
Logical: A partition "Inside" an extended partition, there can be a lot of these!

Seeing as windows **has** to be installed on a primary partition, you should install Linux in an extended partition, to leave space for unexpected guests.

**Separate home**
Lots of people will talk about a "home partition" or a "separate home" - This is because all of their /home folder is on a separate partition.

This is a fundamental addition to any Linux box, as it lets you install a new version without losing your settings and files.

Another great reason to have a separate home is to run more than one linux distrobution. If you are running Fedora and Ubuntu at the same time for example, you can tell them both to run the same home partition, meaning all your settings and files will be cross-OS.

There are other folders some suggest you should separate, but in Ubuntu you can easily create a script that will install all your applications for you, making this irrelevant (And dangerous if you are using outdated apps!)

**Size**
Partitions take longer to mount when they are large, so an ideal partition setup uses smaller partitions.

A swap partition is extra memory for when your ram runs out. Its really up to you, but nowadays its more irrelevant because computers have so much ram... The twice your ram phrase doesn't apply any more.

Greenwidth notes that as of kernel 2.6, a swap file is just as fast as a swap partition, so you may want to leave out the partition and use a file in your root partition instead, which is easier to delete and resize.

audiomick notes that you need a swap partition (not file) equal to or larger than your memory in use to hibernate. so if you expect all 2 gigs ram and some swap to be in use every time you hibernate, you need a swap of 2.5 gigs or so.

2 gigs should be fine for most computers.

The root partition (Everything but the home partition) is about 10 gigs here, but even with lots of apps installed, it only uses 4.1 gigs. 10 gigs should be plenty for all your needs.

The home partition: This ones tricky. Lots of people make their home partition as big as all the space they have left over, but this takes a long time to mount.

Nothing you have will take up that kind of space, give your home about 10 gigs per (active) user, that should be plenty.

Then you create a data partition to keep all the rest of your stuff, so that large files like videos can be stored, but you still get to shave those necessary seconds off your boot time.

**Position**
You computer can be sped up by positioning and sizing the partitions correctly.

The closer a partition is to the heads, the less they have to travel, so the earlier a partition is in the partition table, the faster it will perform.

For this reason I suggest putting the partitions in the following order:

[LIST=1]
[*]Swap (If you are using it)
[*]Root
[*]Home
[*]Data
[/LIST]
Note: If you have an SSD, you can get a HUGE performance boost by installing swap and root on the SSD and using a normal HD for home and data.

**So how do I do it?**
When you are installing, you will come to an option to choose where you want Ubuntu installed on your HD.

Choose "Specify partitions manually"

You will be brought to a special window, where you can edit your partitions to your hearts desire.
[B]
[SIZE=1]** Skip ahead if you don't want to keep your other OS (or don't have one) **[/SIZE][/B]

[LIST]
[*] Right-click the partitions from the other OS, and click *Resize/move*
[*] Resize the partitions towards the end of the partition, so as to give Ubuntu a faster part of the HD to deal with.
[*] If there are already 4 primary partitions, and none of them is extended, you will have to delete one of them, this is up to you, I don't know which partitions are important on your computer.
[/LIST]
    [SIZE=1]**** Stop skipping now! ****[/SIZE]

[SIZE=1]**If you have an SSD switch to it now (upper right)**[/SIZE]
 
[LIST]
[*]Right-click the empty space, and click NEW
[*] Create an extended partition if there is none, leave room for the following.
[*] Create a swap partition if you want it, if you don't, skip this line.
[*] Next, create an EXT4 partition and select to mount it at / (root), make it 10 gigs (at your discretion)
[/LIST]
[SIZE=1]**If you have an SSD, switch to your HD, create another extended partition and continue**[/SIZE]

[LIST]
[*] Next, create an EXT4 partition and select to mount it at /home, again, your discretion.
[*] Finally, if you don't need the space for something else, create a final EXT4 partition, don't mount it, and take up all the space. This is your data partition.
[*] If you wanted a swap file rather than a swap partition, you just create a file of a specific size on your HD:
```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=<megabytes>
sudo mkswap /swapfile
sudo swapon /swapfile
echo "/swapfile swap swap defaults 0 0" | sudo tee -a /etc/fstab
```
[/LIST]
 Congratulations, you now understand partitioning and have a leaner meaner possibly greener machiner!...

**Separate home partition on machine already installed**
To make a separate home partition post-install, you will need to have an Ubuntu live disc (Or similar live disc with partition editing software)

First of all, backup your home folder (This could get messy with a dodgy HD), you can do this by simply pressing ctrl-h (to show hidden files) ctrl-a (to select everything) and right-click > compress. Then send this somewhere safe (USB, other HD, something off this HD)

Once you have booted up, go to System > Administration > Gparted: This is essentially the same program you encountered during the installation.

Your first action will be to shrink an existing partition to make way for the home partition, I suggest shrinking the root partition first.

Next, create an EXT4 partition in the empty space. Click the apply button to save changes. Right-click it and select information, note the UUID field, we will need it later.

Now, mount the root partition, and the new partition, and note their locations in the live file-system. Execute these commands (Making appropriate changes):
```
sudo mv /mnt/<rootPartitionFolder>/home/* /mnt/<newPartitionFolder>
sudo rm -rf /mnt/<rootPartitionFolder>/home/*
echo "UUID=<uuidHere> /home ext4 defaults 0 2" | sudo tee -a /mnt/<rootPartitionFolder>/etc/fstab
```Shrink your root partition to 10 gigs or so, fill in the space with whatever you want (more home?), reboot: your computer should boot as normal, only with a new home partition.

_If it doesn't work, don't say I didn't warn you! _

Uncompress your backed up home to its former location, boot a live disc, delete the new partition, resize the root partition, remove the last line from /etc/fstab, and (at your discretion) start again ;)

**Finale**
If you want to further tweak your HD (For a possible 20x speed increase!) [look up the hdparm utility]("http://linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html"), or install "[sdparm]("apt://sdparm")" (Click to install) for sata drives (Beyond the scope of this guide)

It isn't worth shuffling your partitions around for speed after install, it takes a lot of time and effort, will probably break your system, and will only save a couple of hours of your life (minus the couple you wasted fixing it)

---

### Post by J V on 2010-01-27
Oh dear, wasn't meant to actually post, would some mod please move to tips/tutorials and rename to "Hard-drive tips" please? :oops:

---

### Post by Greenwidth on 2010-01-27
Nice guide.
One small thing you could also mention is that as of the 2.6 kernel: "a swap file is just as fast as a swap partition."
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you need to move or resize your swap it is much easier as a file rather than a partition.

---

### Post by J V on 2010-01-27
Thanks, added!

---

### Post by Psumi on 2010-01-27
> **J V said:**
> Oh dear, wasn't meant to actually post, would some mod please move to tips/tutorials and rename to "Hard-drive tips" please? :oops:

When you post to tutorials and tips, it is SUPPOSED to not allow you to post the topic, moderators have to moderate posted topics before they appear.

Don't go posting them in other forums on this board just to get around that :|

---

### Post by J V on 2010-01-27
I only wanted to preview it before I posted to tips & tricks, sorry :-x

---

### Post by Diametric on 2010-01-27
Great information!  Any chance a section could sspeak on what, if anything  one could do if they have already installed and would like to place their home directory in a separate partition? Or better yet, can some one who has already installed, perform ANY of the things you post?  

Cheers!  And thanks again for the post.

---

### Post by J V on 2010-01-27
Thanks for the praise, got 2 others (one in queue in t&t other in tomboy here, will post when first gets through)

I keep them in tomboy to paste to the very very common asked questions on these forums :P

It should (theoretically) be possible to do it after install, I will write up a small paragraph then.

---

### Post by underquark on 2010-01-27
"You will be brought to a special window..."

Sounds vaguely creepy.

"If you want to further tweak your HD (For a possible 20x speed increase!) look up the hdparm utility (Beyond the scope of this guide)"

Does that guide (written in 2000) still apply to modern SATA drives?
__________________

---

### Post by J V on 2010-01-27
Yes, but you need sdparm for that, I will note that there...

---

### Post by audiomick on 2010-01-27
Hi.
Seems pretty good, except the bit about swap.

The swap = 2xRAM rule can be labelled as obselete rather than BS. From what I have read, it dates back to times when RAM sizes were significantly smaller than today. It is proving to be persistant, which is why I think it is good to explain the background.

You are right that even with 2 GB of RAM, you will not even scratch your swap most of the time. I have 4, and I don't think my RAM has ever seen a single electron... :)

However, you should mention that hibernate needs a swap partition (not a swap file) to work. The function effectively writes the contents of RAM to the swap partition
from this page:
[https://help.ubuntu.com/community/PowerManagement/Hiberate](https://help.ubuntu.com/community/PowerManagement/Hiberate)

> The s2disk program does the following in order to hibernate the machine:

   1. Tell the kernel to create a snapshot of the current system state.
   2. Read the snapshot data from the kernel and write it to the swap partition, possibly encrypting and compressing the data.
   3. Power off the machine. 

When next you power up, the reverse happens:

   1.  After a basic system boot, but before mounting any partitions, resume runs from the initrd.
   2. The snapshot data from the swap partition is read (and possibly decrypted and decompressed).
   3. resume tells the kernel to restore the snapshot.
   4. the kernel returns at the place it was before the hibernation. 

Therefore, to be sure that hibernate can work, the swap partition should be equal to (a fraction larger than?) the RAM size.

If the computer will never be hibernated, then the size of the swap space is of course purely a matter of choice.

---

### Post by J V on 2010-01-27
I see, it won't work with swap file?...

What if you have 1 meg in swap and 1 gig in ram with 1 gig swap when you hibernate?

This could get complicated :P

---

### Post by gabo.cr on 2010-01-27
> 
For this reason I suggest putting the partitions in the following order:

   1. Swap (If you are using it)
   2. Root
   3. Home
   4. Data


I didn't know the order was important.
:-k

I always do:

/root
/home
/swap

---

### Post by J V on 2010-01-27
think of it this way: the head has to travel to the data to collect it, if the data is right next to the head, it will take a lot less time to get it than if it has to travel all the way to the outside of the HD. Because of this, data closer to the head (beginning of the HD) can shave a couple of seconds off boot time etc...

But yeah, if you already have that order, it isn't worth reordering unless you wanted to do a complete wipe anyway :)

---

### Post by Gone fishing on 2010-01-27
I've got /home /root and /boot partitions. Why, because I use the GAG boot manager (currently running Ubuntu, PC-BSD, Haiku and Windows 7) and it doesn't like ext4 so my small /boot partition is ext3

---

### Post by hhlp on 2010-01-27
i read that in a extreme security linux instalation separete that:

/root
/swap
/home
/var
/temp

---

### Post by J V on 2010-01-27
Well if you need a separate boot manager you should already know how to partition, so I'm not putting that in...

root: Theres nothing in it on ubuntu anyway
var: There may be lots of logs, but this isn't a high priority server we're talking about, logs aren't really necessary
temp: I think you mean tmp, but all that holds under ubuntu is flash videos and the like, and how important are they? :P

---

### Post by brookie on 2010-01-28
Hello JV,

Very nice post! 

I have a question though. I am doing a reinsatll of Karmic and I will also install virtualbox with WInXP Pro SP3. 

If installing virtualbox puel with WinXP 10GB - 12GB virtual disk in /home means I would have to make my /home dir the original 10GB + 10GB for WinXP in virtualbox? 

This is what I'm thinking because last time I installed virtualbox it installed in /home directory. 

Let me know what you think. I'm ready for a new install of Karmic because I've partitioned this disk to hell already. Just trying to start out fresh from your suggestions with:

10G / - ext4 primary
10GB /home - ext4 primary
208.9GB for data - ext4 logical
4GB /swap (i have 2GB ram) -swap logical

Thanks in advance.

Cheers,
brook

ps...this is what it's looking like now:
4 /swap - logical
10 / - primary
22 /home - primary
196.9 logical for data (no mount point)

pss... Also, do I need a mount point for my data partition? I get an error if I don't set one. 
No mount point is assigned for the ext4 file system in partition #4...
If you do not go back to the partitioning menu and assign a mount point from there, this partition will not be used at all.

---

### Post by J V on 2010-01-28
Well I don't know why you are getting the error, it should just show up in your places and be ready to mount when you click on it.

As for the virtual drive, yes, it likes to put them in home, so either make a larger home, or mount the data partition when you want to boot Virtualbox.

4 gig swap seems a bit over the top, but then again, if you are planning on hibernating with windows in a vBox it might be necessary sometimes ;)

I would still only use 2 gigs though, I have never dipped into my swap partition so far :)

---

