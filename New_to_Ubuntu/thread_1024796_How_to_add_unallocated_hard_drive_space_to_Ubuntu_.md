---
title: "How to add unallocated hard drive space to Ubuntu partition"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by satans aunt on 2008-12-29
Apologies if this is a ditzy question or has been covered elsewhere.


Is there a way for me to add unallocated hard drive space to my Ubuntu partition without interfering with a perfectly functioning operating set-up???



Also, is it possible to reduce the size of my Windows partition so as to add even more hard drive space to the Ubuntu partition???

Thanks

---

### Post by nhasian on 2008-12-29
sure if you are using windows vista:

How to Shrink a Partition in Vista:
1. Press Win+R to open the run box
2. Type in diskmgmt.msc and click OK
3. Right-click on the partition you wish to shrink
4. Select Shrink Volume…

if you are using a previous version of windows, then you should boot off the ubuntu liveCD and shrink the partition with gparted in System->Administration->Partition Editor.

---

### Post by thane1 on 2008-12-29
Not ditzy at all.  I'll comment on your first question.  Just one way of doing it.  You could use some or all of your unallocated space to form a new partition (you could use gparted for instance available through the repositories in Synaptic, which will then be available through your System-Administration menu.)  This new partition could then be set to handle your /home directory, where your personal files are kept.  There are a lot of posts on the forums about how to do this.  If your present unallocated space is large enough to handle your present and somewhat future needs, this will also enable you to change your Ubuntu versions with clean installs, while keeping your /home separate - much easier than having to copy all of your data over to a new, large partition shared with your newer operating system.

---

### Post by Elfy on 2008-12-29
If you have default ubuntu setup it's likely that you will need to resize the extended partition first.

You will need to turn swap off - you can do that from the partition editor.

---

### Post by thane1 on 2008-12-29
If you did decide you wanted to separate your /home from your Ubuntu operating system, here's an Ubuntuforums tutorial, which might help out a bit.  Just saw it but it looks pretty thorough.  Cheers

[http://ubuntuforums.org/showthread.php?t=282018&highlight=%2Fhome+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=%2Fhome+partition)

---

### Post by satans aunt on 2008-12-29
:)

---

### Post by satans aunt on 2008-12-29
Update.

So it turns out the unallocated hard drive space was only a few GBs (2.8) so I opted to convert into a 'linux-swap' partition.

I still plan to reduce to the size of my Windows partition, seeing as how I've found no reason to use Windows for two weeks- If I unmount my Windows partition will I then be able to reduce its size and add the surplus to my Ubuntu partition?

Is it possible to unmount without causing damage to the data within the partition?


Thanks

---

### Post by mkvnmtr on 2008-12-29
The best way is to boot from the live disk you used to install and do it from the partition editor an the disk. Your partitions will not be mounted and you should have internet if you need to ask a question.

---

