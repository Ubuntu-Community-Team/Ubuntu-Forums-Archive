---
title: "What format is best for USB external Hard Drive"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Scunnered on 2009-01-04
I earlier was experimenting with a USB external HD as I had hoped that I could use it as a stand along drive for Linux.  I kept getting problems and eventuially gave up in disgust.

Subsequently she who must be obeyed has advised me that her photographs are too much for a DVD and wishes me to save these to the USB HD.  As the HD currently has 8.04 installed I will have to reformat the drive to work with doz.  I have been considering finding more about working with photographs so my thought was that if the drive is formated in such a way that I can take and extract photos from it into Ubuntu 8.10 I can then see how I can get on with things.

Can you please advise which format i should adopt to be able to achieve this aim.

Thanking you in anticipation.

---

### Post by PeeZz on 2009-01-04
If you use the HD to transfer files from different OSes I'd recommend you to use FAT32 or NTFS, because almost all OSes can read & write from those formats.

You can't install Ubuntu on those formats ( I think ) so you'll have to partition the disk.

---

### Post by fela on 2009-01-04
I wouldn't worry about whether it'll be readable by Ubuntu. I've never had a drive unreadable out of the box with Linux/Ubuntu on any format, be it FAT16, FAT32, NTFS, ext2, ext3, HFS(plus), ISO9660, etc etc etc.

---

### Post by zcecc22 on 2009-01-04
If you decide to go with FAT make sure the 4gb size limit does not bother you. For example, working with pictures from a digital camera should be fine but then mastering a DVD with them to display on your TV could be a problem.

Cheers

---

### Post by PeeZz on 2009-01-04
> **fela said:**
> I wouldn't worry about whether it'll be readable by Ubuntu. I've never had a drive unreadable out of the box with Linux/Ubuntu on any format, be it FAT16, FAT32, NTFS, ext2, ext3, HFS(plus), ISO9660, etc etc etc.

But it could prevent problems on a windows machine :)

---

### Post by fela on 2009-01-04
> **PeeZz said:**
> But it could prevent problems on a windows machine :)

That's what I mean - the only problems will be windows based, as ever :P

---

### Post by Scunnered on 2009-01-05
My thanks to you all for your replies.

I connected the HD up to doz and it duly acknowledged that it was connected but would it permit anything to be done to format it NO. I can read the drive OK in 8.10 but the data shown on the drive does not display in doz.

Is there a way that I can format the drive to suit doz or alternatively totally erase all data on the USB drive to let me try again.

It is so frustrating that any involvement with doz creates more problems than solves any.

---

### Post by howefield on 2009-01-05
From 8.10 use gparted to format the drive to ntfs, if you haven't got gparted on your machine, you'll get it with Synaptic Package Manager.

You should be able to do this with the data on the drive, but it is likely to take a while.

---

### Post by cjv8888 on 2009-01-05
You should be able to use Gparted in 8.10 to erase the partition in the USB drive and then format it as NTFS or FAT32.

---

### Post by Scunnered on 2009-01-05
Many thanks to you both howefield & cjv8888.

I will take your advice on this and see what happens. 

I follow cjv8888 in I am Ubuntu-ing but when she who must be obeyed speaks I quake in my shoes and get on with things.  Anything for a peaceable life !

---

### Post by theacerguy on 2009-01-05
i would jst half ext3 half ntfs i had to as my pc's wouldnt write to ntfs so i had to dual partition cos my windows cant recognise ext3(well kinda obvious)

---

### Post by cjv8888 on 2009-01-05
> **theacerguy said:**
> i would jst half ext3 half ntfs i had to as my pc's wouldnt write to ntfs so i had to dual partition cos my windows cant recognise ext3(well kinda obvious)

That's strange because Ubuntu can generally read and write to NTFS and FAT unless something has gone wrong with the installation.

---

### Post by howefield on 2009-01-05
> **theacerguy said:**
> ......so i had to dual partition cos my windows cant recognise ext3(well kinda obvious)

There are utilities available which allow windows os to read and write ext2/3 partitions, I can't vouch for how good they are, but they are there.

---

### Post by PeeZz on 2009-01-05
If you want to use gparted to format your drive to ntfs don't forget to install ntfsprogs too.
See this [table]("http://gparted.sourceforge.net/features.php") for more information.

---

### Post by wizard10000 on 2009-01-05
I generally use FAT32 for shared partitions.  NTFS write support in Linux is and probably always will be experimental.

---

### Post by theacerguy on 2009-01-05
i have heard of win ext3 but its my mums laptop so she wont let me install things like that anyway i wasn't refering to ubuntu i was refering to linpus on my aspire one(ok so its ubuntu now) which doesn't write to ntfs

---

### Post by insane_alien on 2009-01-05
why are people mentioning FAT32? FAT32 should hae died a horrible painful death long ago.

ntfs-3g is pretty much bugfree, just don't enable ntfs compression or encryption on the drive and it will be both readable and writable in both ubuntu and windows.

i've been using it heavily for over a year now and not a single file has been corrupted when writing to ntfs, well, thats a lie, but the only time there was corruption that was because i tripped over it and yanked the cable out, but the same thing would have happened for anything else.

---

### Post by Scunnered on 2009-01-05
I attempted to work with gparted only to get confused.  When I open gparted I can clearly identify the USB external HD and is is shown as /dev/sdb. Currently if I mount the drive I can see all the folders associated with 8.04 version.

When I view the partition it shows all the drive space as being unallocated and attempting to use create partition table I am warned that all data on the drive will be lost. Clicking create shows a very quick movement on the progress bar but when I go back and mount the drive everything was as before.

When I look again at the gparted display edit and partition sections are greyed out and everything on the line below is also greyed out.

Can anyone offer guidance as I am not getting to grips with the problem.

Thanking you in anticipation

---

### Post by PeeZz on 2009-01-09
I think the drive should not be mounted.

So first attach the drive to your pc, it will mount automatically. Then right click it and select unmount, but leave it attached to your pc :).

Then you should be able to partition it.

---

### Post by Hallvor on 2009-01-09
Use Ext3, not the dinosaur FAT32 or NTFS. The NTFS driver for linux seems to work just fine, but NTFS is still closed source, and ntfs-3g is still a reverse engineered hack.

Ext3 is open source, and since it is open source it can be read perfectly on both linux and windows. That means you get to run the most advanced file system from both linux and windows - perfectly.

Don`t let the name ext2 scare you, since it also works on ext3.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Scunnered on 2009-01-10
My thanks to each and everyone for your contributions.

I do not know what I have done but what ever it was it is terminal. I am totally unable to have either my Linux or XP machine to register the fact that the USB Drive was connected.  It would appear that I have totally killed the drive and as such I am now looking at alternatives to my storage problem.

Concidentally one of the magazines I was reading today suggested that it could be an idea to use an old system purely for storage. I might just give this a try before I splash out more cash.

Once again many thanks

---

