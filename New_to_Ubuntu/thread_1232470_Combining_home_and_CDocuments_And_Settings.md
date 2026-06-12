---
title: "Combining /home and C:\Documents And Settings"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by InfectedWithDrew on 2009-08-05
I am looking to combine the directories in the topic into one partition.  I'm not sure if it's possible since you can't use ntfs for /home, but...

Explanation: I want to have My Documents in Windows be integrated with /home in Ubuntu.  That way, I don't have to partition my 500GB internal drive that I set aside for documents and music and such, I can just have everything draw from one source.

So, what would be the best solution for this?  I know about ext2fsd for Windows, but I'm not sure that it would work... doesn't it mount the drives after Windows boots?

Some more info: I'm using Ubuntu 9.04 64-bit and Windows 7 RC 64-bit.

---

### Post by sdlynx on 2009-08-05
I think if you make your Ubuntu home partition ext2 you can use IFS Drives to mount it (read/write) easily.  Then, you can go into the windows registry and change it so that your Documents/Music/Videos folder paths are directed towards your /home partition folders.  Take a look at this: [http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/](http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/)

I know its for virtualbox but it integrates kind of the same idea.

---

### Post by BDNiner on 2009-08-05
I don't see any reason that you can't use NTFS for /home, you can in linux mount /home to a separate partition so that part is solved. Your biggest problem is keeping c:\documents and settings\username on a separate partition. I know you can redirect folders in My Documents to other locations but not all of C:\documents and settings\.

---

### Post by jerome1232 on 2009-08-05
Personaly I would make the relative folders in /home symlinks to the ones on your windows system.

ie

Documents -> /media/windrive/user/youruser/My Documents

and etc.

You make links like this:

```
ln -s target link name
```

so if I wanted to make the above link:

```
ln -s /media/windrive/user/youruser/My\ Documents ~/Documents
```

---

### Post by sdlynx on 2009-08-05
> **jerome1232 said:**
> Personaly I would make the relative folders in /home symlinks to the ones on your windows system.

ie

Documents -> /media/windrive/user/youruser/My Documents

and etc.

You make links like this:

```
ln -s target link name
```

so if I wanted to make the above link:

```
ln -s /media/windrive/user/youruser/My\ Documents ~/Documents
```

sounds like a good alternative if my idea doesn't work.

---

### Post by InfectedWithDrew on 2009-08-05
> **sdlynx said:**
> I think if you make your Ubuntu home partition ext2 you can use IFS Drives to mount it (read/write) easily.  Then, you can go into the windows registry and change it so that your Documents/Music/Videos folder paths are directed towards your /home partition folders.  Take a look at this: [http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/](http://ubuntu-tutorials.com/2008/02/01/how-to-do-seamless-window-integration-with-ubuntu-virtualbox/)

I know its for virtualbox but it integrates kind of the same idea.Doesn't ext IFS required an inode size of 128 or something and modern Ubuntu distros use 256?  I remember this problem happening before and my having to use ext2fsd, which is compatible but slow and doesn't even write half the time.

> **BDNiner said:**
> I don't see any reason that you can't use NTFS for /home, you can in linux mount /home to a separate partition so that part is solved. Your biggest problem is keeping c:\documents and settings\username on a separate partition. I know you can redirect folders in My Documents to other locations but not all of C:\documents and settings\.I am sitting next to my computer during the installation and as I try to map /home to a ntfs partition it only gives two options for what I can map: /dos and /windows.  But as to your other point, I'd settle for just moving My Documents.

> **jerome1232 said:**
> Personaly I would make the relative folders in /home symlinks to the ones on your windows system.

ie

Documents -> /media/windrive/user/youruser/My Documents

and etc.

You make links like this:

```
ln -s target link name
```

so if I wanted to make the above link:

```
ln -s /media/windrive/user/youruser/My\ Documents ~/Documents
```That sounds like a good idea, so I'd basically install Ubuntu ignoring mapping /home at first and then I'd do those commands later?  I'll do that if no easier solution exists (and that's a pretty easy solution, I think).

---

### Post by jerome1232 on 2009-08-05
> **InfectedWithDrew said:**
> 
That sounds like a good idea, so I'd basically install Ubuntu ignoring mapping /home at first and then I'd do those commands later?  I'll do that if no easier solution exists (and that's a pretty easy solution, I think).

Yes, and you actually have to delete the folders in your home folder prior to making the symlinks.

---

### Post by BDNiner on 2009-08-05
I was wrong, you cannot mount /home to an ntfs partition. You can only mount folders in your home to an ntfs partition using fstab

---

### Post by InfectedWithDrew on 2009-08-05
> **BDNiner said:**
> I was wrong, you cannot mount /home to an ntfs partition. You can only mount folders in your home to an ntfs partition using fstabOkay, thanks anyways!  I was about ready to just type /home into the partitioner...

> **jerome1232 said:**
> Yes, and you actually have to delete the folders in your home folder prior to making the symlinks.Okay, thank you, I'll try this solution and post back if it works or if it doesn't.

---

### Post by bugritall on 2009-08-05
I have a 10GB NTFS partition called Knoxx where I keep all my vital data - things like documents, programming source, e-mail and the like. 

On Windoze: 
My Documents contains only a link to the store on Knoxx
BCB and other important tools are configured to store their files on Knoxx.
Thunderbird and Firefox's *profile.ini* files have been redirected to their stores on Knoxx.
It's fairly easy to adjust things even if Windoze reallocates Knoxx's drive letter.

On my Jaunty and Karmic installations:
Pretty much as above, really, minus the drive letter problem.

This has an enormous advantage in that I can (almost) cheerfully wreck anything that isn't in Knoxx and no real harm results. Furthermore, all my OSs use Thunderbird and Firefox and they all access the *same* stores on Knoxx, so no more wondering where that e-mail or bookmark disappeared to when I log on to a different OS.

It took a bit of setting up but it's truly been worth the effort.

---

### Post by CatKiller on 2009-08-05
> **jerome1232 said:**
> Personaly I would make the relative folders in /home symlinks to the ones on your windows system.

Bit late to the party, but that's what I'd do, too.

As an alternative to the rather less elegant mount-an-NTFS-partition-somewhere-and-just-dump-stuff-in-it.

Anything else leads to madness.

---

### Post by InfectedWithDrew on 2009-08-06
Thank you very much to jerome1232, it seems to be working.  Though I haven't tested accessing these folders BEFORE the NTFS partition is mounted.

---

### Post by InfectedWithDrew on 2009-08-06
Update: after a reboot all my symlinks broke.

How can I make this not happen?

---

### Post by jerome1232 on 2009-08-06
They are probably broke because the partition isn't mounted, make it mount automatically by editing fstab.

There are some gui's around to make editing fstab easy but I don't know what they are (pmount or something I think)

Otherwise have a look at the fine Ubuntu community documentation about it.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

ask questions if you need help.

---

### Post by InfectedWithDrew on 2009-08-07
All right, I'll do the fstab thing.

Another question, made a [new thread](http://ubuntuforums.org/showthread.php?p=7746570) since it seemed irrelevant, but is actually part of my situation still: I'm trying to VM my other system but I'm not sure if I can have a VM touch the same partition as the host.

---

### Post by InfectedWithDrew on 2009-08-09
> **jerome1232 said:**
> They are probably broke because the partition isn't mounted, make it mount automatically by editing fstab.

There are some gui's around to make editing fstab easy but I don't know what they are (pmount or something I think)

Otherwise have a look at the fine Ubuntu community documentation about it.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

ask questions if you need help.

Which options should I use?
Or rather, I'll explain.
I set /mnt/data to be to where this drive should be mounted.  The drive exists at /dev/sdb1.  The label is data.  What should I put in fstab to get this to mount automatically and work without any snags?

---

### Post by jerome1232 on 2009-08-09
I'd prbly do something like

```
/dev/sdxy /my/mount/point ntfs umask=000 0 0
```

umask=000 sets the permissions of files and folders to 777 or rwxrwxrwx.

The last two zero's tell the system not to run a routine disk check on the partitionl


edit: it's better to go by uuid rather then device. Use sudo blkid to find the uuid for your partition and just put that instead of the device path, all your other entries should be using uuid's so use those as an example.

---

### Post by InfectedWithDrew on 2009-08-14
> **jerome1232 said:**
> I'd prbly do something like

```
/dev/sdxy /my/mount/point ntfs umask=000 0 0
```

umask=000 sets the permissions of files and folders to 777 or rwxrwxrwx.

The last two zero's tell the system not to run a routine disk check on the partitionl


edit: it's better to go by uuid rather then device. Use sudo blkid to find the uuid for your partition and just put that instead of the device path, all your other entries should be using uuid's so use those as an example.Thank you, your blkid idea worked but I'd like to say that your options were a little wonky.  This worked for me (for future reference):

```
UUID=067D2AEA63719111 /mnt/data ntfs-3g auto,rw,suid,dev,exec,user,async,umask=000 0 0
```

---

### Post by bugritall on 2009-09-18
I'm an habitual system fiddler, so my drive and partition IDs get reassigned from time to time. Identifying my partitions by their UUIDs takes care of that, of course, just like it's supposed to. The only gripe is that UUIDs are cumbersome and non-intuitive and they change whenever I reformat a partition.

However, there is a neat way to avoid messing about with UUIDs almost entirely, simply by using partition labels instead. It's easy to label your NTFS partitions in Windoze and you can label your Linux partitions like this:
```
sudo e2label /dev/sdxy *partition_label*
```Assuming that you have already created /mnt/*partition_label,* you can mount your NTFS partitions in fstab like this:
```
LABEL=*partition_label* /mnt/*partition_label*  ntfs auto,users,defaults 0 0
```Furthermore, you can specify your partitions in Grub's menu.lst in pretty much the same way. *kernel* entries that look like this:
```
kernel        /vmlinuz-2.6.28-13-generic root=UUID=f16f4c8a-e725-45bc-92c1-84c8b6337245 ro quiet splash 
```can be edited to look like this:
```
kernel        /vmlinuz-2.6.28-13-generic root=LABEL=ubuntu ro quiet splash 

```So, provided you label your partitions in a consistent manner, you can even get away with a reformat without having to delve into fstab again.

Finally, it might be worth mentioning that you can restore a former (or any other) UUID to a partition, after it's been reformatted:
```
tune2fs -U *its_former_uuid* /dev/sdxy
```

---

### Post by bugritall on 2009-09-18
> **InfectedWithDrew said:**
> Which options should I use?
Or rather, I'll explain.
I set /mnt/data to be to where this drive should be mounted.  The drive exists at /dev/sdb1.  The label is data.  What should I put in fstab to get this to mount automatically and work without any snags?
For something even easier and less prone to trouble, append this to fstab:
```
LABEL=data /mnt/data  ntfs auto,users,defaults 0 0
```You can even reformat the partition, provided you give it the same label again afterwards.

---

