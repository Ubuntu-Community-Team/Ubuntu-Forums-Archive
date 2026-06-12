---
title: "Configure 9.04 for a Single Drive - No other OS"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by troutdog8 on 2009-08-25
Hi,
I am a rank newbie to Ubuntu; I installed Jaunty about 6 weeks ago after an attempt to restore Vista failed.  I was lucky enough to have downloaded a copy of Ubuntu two days prior - literally.  If the questions below are answered elsewhere, I'm sorry for re-asking; I must have missed some threads when I looked.
 
I have used pcs since the early 90s, so I am quite familiar with pc platform, but very much from a microsoft user's standpoint.  I think of drives having letters, etc.
The laptop I installed to has a 160 (or so) hd installed.  It currently has 3 partitions: 
- 10 gb for a restore partion - should have vista on it but fails when I try to restore
- 75 gb for the C drive (this is what *ought* to get restored)
- 75 gb for a D drive, which is untouched in the restore process so user's files don't get lost.
 
I have 4gb of RAM, having upgraded with hopes of getting Vista to perform at a minimally acceptable level.  I was unable to achieve that....  :)
 
When I installed Ubuntu I put it on the C partition (forgive me for using this nomenclature - I realize it doesn't quite apply in linux) and left the other two alone, and things seem to be working fine.  The "D" partition is available in Ubuntu, the 10 gb is not. I understand that there is 10 gb sitting unused on my drive - I can live with that for the moment.  
 
After the installation I got a message about not setting up a swap partition and performance being affected, but I must have missed (or misunderstood) the opportunity to do so during the install.  I haven't gone back to reinstall or repartition or anything, since I don't really understand the implications, and things seem fine as they are.
 
I am planning to purchase a new hard drive in the near future - probably 320 or 500 gb.  Can someone advise me on how to best configure 9.04 on a sinlge drive?  I somewhere here I saw a recommendation of 500 mb for the swap partition.  Should I split my drive in two - 500mb for the swap and the rest for the OS?  Is it better to somehow divide the drive further?  I read a reference to setting aside 8gb for the OS.  I would assume the remainder of the drive would be a single partition for programs, data, etc?  8 gb seems kind of small, esp with hundreds of g available, but...rank newbie.
 
I am not interested in a dual boot situation.  I don't have a useful copy of Windows right now, and even if I did I'm frankly ready to move on.  I basically want to configure a single drive to best run Ubuntu.
Also, should I use ext3? 4?  Do all partitions get the same filesystem? (I would assume so).
 
I'm sorry for rambling, but I'm new to this and really excited about it.  Thank you in advance for any suggestions!
Richard

---

### Post by Big_astur on 2009-08-25
When people say 8GB for ubuntu means that the rest(if u don't create more partitions) would be to mount your Home.

So when u install it, u select manual to manage the partitions. U create one for the swap, another with 8-10GB (ext4, or what u want) for "/" and the rest for "/home"

---

### Post by halitech on 2009-08-25
when you are partitioning you can set up to 4 primary partitions (same as in Windows) but each primary can have more extended partitions inside.

As far as how to split it up, thats up to you. Most seem to be of 1 of 2 minds, just have a single / with everything inside it. Others will create a seperate root ( / ) and a seperate /home. I have a 160gig drive for my mine drive and a 320 as a second drive. I created a 28gig / partition, a 2gig swap partition and the rest for /home. My secondary drive is split to a small partition for NTFS (was using it in an external case until the controller died) and the rest ext3,

28gig is huge for / as I'm only using 4.1gig but wanted the extra space just in case.

just as an example:
```
daryl@debian:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              28G  4.1G   23G  16% /
tmpfs                 881M     0  881M   0% /lib/init/rw
udev                   10M   92K   10M   1% /dev
tmpfs                 881M     0  881M   0% /dev/shm
/dev/sda2             118G   28G   84G  25% /home
/dev/sdb2             289G  168G  107G  62% /home/daryl/storage
```

Anything that doesn't start with /dev is inside /

---

### Post by brunogirin on 2009-08-25
There are many ways to do this.

First, the simple way. When you install Ubuntu, it will give you the option to use the whole drive. If you select that option, it will wipe out the drive and automatically create a root (/) partition and a swap one. It will choose a reasonable size for swap (depending on how much RAM you have) and use the rest for a single large / partition.

A more complicated option is to do the partitioning yourself, if you want to separate the OS from your personal files: this can be useful if you want to re-install at any point without touching your own data.

In this case, the most standard setup is to create a swap partition, a / one and a /home one. Make the swap partition about the same size as the amount of RAM you have. The / partition can be as small as 4GB but make it 10GB to be comfortable. Then everything else for /home. The OS will go in / and your personal files in /home.

As pointed out by halitech, you can only have 4 primary partitions per physical disk but you can go beyond that limit using extended partitions. If you want to do that, create swap and / as primary partitions, then create an extended partition that covers the rest of the disk and create the /home partition inside the extended partition.

In terms of the file system you use, I would suggest you use ext4: it's faster than ext3 and even though it's quite recent, I haven't had any issue with it.

To finish, a quick intro to the Linux file system (for info, feel free to ignore it if you don't find it clear). Linux doesn't have drive letters, it just has a single file system, where the root directory is called /. Underneath that directory are a number of standard directories like /usr, /bin, /var, /home, etc. By default, each directory is hosted on the same disk partition as its parent, unless specified otherwise. You can decide that /home should be hosted on a different partition than /. For example, you could have / mounted on /dev/sda1 and /home mounted on /dev/sda2. In this case, everything that is in /home or a subdirectory of it will physically be in the /dev/sda2 partition; everything that is under / but not in /home will be physically located on the /dev/sda1 partition. Each individual partition can use its own specific file system: you could have ext3 for / and ext4 for /home if you wanted to. You could have /home on a different hard disk altogether, or even on a different server by using nfs. This is extremely powerful because it allows you to keep the same file directory structure whether your system is all on one big partition or split between several disks or even network devices.

---

### Post by mkvnmtr on 2009-08-25
Changing to linux can be confusing because the partitions have different names. I would recommend that you install the program Gparted. You are not going to use it on your disk bvut when you open partition  manager you will be able to see your partitions and what they are called in Ubuntu.Study them until you understand what you are looking at. Ask the questions you need to to understand. Then decide what you wish to do to your hard drive.

I install Ubuntu with a root partition of about 7 Gb and a home partition of what ever is left but you will need to decide how you wish to do it.

If you have a partition that is not being used you might practice making it smaller. Boot up the live disk and use the partition editor on it. Be sure to back up your stuff before you start.

If it was me after I felt I could use the partition editor I would boot the live disk and do a reinstall using the manual partition mode but you may wish to do it another way.

Just make sure you ask all your questions before you start. It is really not hard but different and easy to do the wrong thing if you are in a hurry.

---

