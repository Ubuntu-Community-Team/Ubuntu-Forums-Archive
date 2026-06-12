---
title: "Formatting External Drive and Choosing A File System"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by completeidiot on 2010-01-16
I have an external drive that is currently split into one fat32 and one mac partition. the mac partition has been very unstable (frequently switches into read only and stays there) and I have decided that i don't want to deal with it any more. my questions are...

Is Fat32 the best option as far as widespread compatibility and stability?

What is the best way to convert the drive? I'm assuming this must be a two step process of formatting and then converting....right?

Thanks

---

### Post by OlyPerson on 2010-01-16
Linux compatibility with NTFS filesystems has become very good, maybe try looking at that for ones compatible with windows/linux/mac.

I've always used GParted for partitioning/formatting, but I believe Disk Utility might also work for this.

Also note that the max file size in FAT32 is 4GB, so if you're storing high definition video or anything large on there good luck.

---

### Post by RedRat on 2010-01-16
Depending on your environment (e.g., are you on a home or SB network, what kind of access do others need, etc.) you would be far better off with NTFS. I have a 500Gb drive on my linux machine that was formatted with NTFS so that Windows machines could read the files. Ubuntu (and I am using 8.04) reads NTFS and writes to NTFS with no problems that I have seen. A year ago that was not quite the case. So if you are on a mixed network, then go with NTFS. Fat32 is pretty much passe now.

---

### Post by completeidiot on 2010-01-17
It's a 1 terabyte external drive that is full of music. It's primarily being used on a netbook running UNR....but I really can't predict what devices i will want to access the data from in the future.
So I have a +1 for fat32 and a +1 for NTFS?
Also looking for recommendation on method of changing the drive over to whichever system I choose....

---

### Post by kenuf on 2010-01-17
NTFS allows for larger file sizes than FAT32 (will matter if you start working with full DVD ISOs), and it allows for more permissions controls.

If you may want to use Windows computers to access the data....  I'd say NTFS.

---

### Post by completeidiot on 2010-01-17
ntfs it is
is there any mac compatability with ntfs?
what's the best way to go about making the switch?

---

### Post by warfacegod on 2010-01-17
If you are going use it only on Linux go with ext4. If you wish to use it on multiple OS types then NTFS is your best option.

Using Gparted to format the drive is your best choice assuming you do it on an ubuntu machine. Do you intend to leave it as two partitions?

I'll walk you through the process if you need any help. (But not 'til tomorrow for I am off to my nightly rest.)

---

### Post by completeidiot on 2010-01-17
ntfs it is. I'm sure i will need to use it on other systems at some point.
i would appreciate the help with the process. I was really thinking that I would probably just have one partition this time around. thanks

---

### Post by warfacegod on 2010-01-17
> **completeidiot said:**
> ntfs it is. I'm sure i will need to use it on other systems at some point.
i would appreciate the help with the process. I was really thinking that I would probably just have one partition this time around. thanks

I strongly suggest using Gparted for this. If you don't have it, installing from a Terminal is easiest:

```
sudo apt-get install gparted
```

First you will need to make certain you have all of the files, you wish to keep, backed up somewhere else. In fact making copies of everything you value on the entire drive would be a wise move. There is always a possibility of file damage.

Using Gparted, you will need to delete the partition you wish to be rid of. Right click it and select delete. Apply the operation by clicking the green check mark on the top left.

---

### Post by completeidiot on 2010-01-17
I backed up everything. I intend to wipe out both partitions and then start over with one massive ntfs partition....90% of the data i will put on this drive will be audio. but i am somewhat considering creating a video and photo partition

---

### Post by blevault on 2010-01-17
> **RedRat said:**
> Depending on your environment (e.g., are you on a home or SB network, what kind of access do others need, etc.) you would be far better off with NTFS. I have a 500Gb drive on my linux machine that was formatted with NTFS so that Windows machines could read the files. Ubuntu (and I am using 8.04) reads NTFS and writes to NTFS with no problems that I have seen. A year ago that was not quite the case. So if you are on a mixed network, then go with NTFS. Fat32 is pretty much passe now.
 
I have two drives in my system.  The first is 250GB, but the machine is old enought that it doesnt recognize the full drive.  So created a 40GB root directory as Linux filesystem, is it possible to partition the remaining drive (minus the swap) as a windows format?  
 
Also the second drive is not used because I was unsure how to format and unsure of where to mount.
 
Any thoughts on this?

---

### Post by warfacegod on 2010-01-17
> **completeidiot said:**
> I backed up everything. I intend to wipe out both partitions and then start over with one massive ntfs partition....90% of the data i will put on this drive will be audio. but i am somewhat considering creating a video and photo partition

Creating separate folders in the drive is an option as well.

---

### Post by warfacegod on 2010-01-17
> **blevault said:**
> I have two drives in my system.  The first is 250GB, but the machine is old enought that it doesnt recognize the full drive.  So created a 40GB root directory as Linux filesystem, is it possible to partition the remaining drive (minus the swap) as a windows format?  
 
Also the second drive is not used because I was unsure how to format and unsure of where to mount.
 
Any thoughts on this?

That can be done in Gpared.

---

### Post by completeidiot on 2010-01-17
> **warfacegod said:**
> I strongly suggest using Gparted for this. If you don't have it, installing from a Terminal is easiest:

```
sudo apt-get install gparted
```

First you will need to make certain you have all of the files, you wish to keep, backed up somewhere else. In fact making copies of everything you value on the entire drive would be a wise move. There is always a possibility of file damage.

Using Gparted, you will need to delete the partition you wish to be rid of. Right click it and select delete. Apply the operation by clicking the green check mark on the top left.

then what?

---

### Post by warfacegod on 2010-01-17
> **completeidiot said:**
> then what?

Have you decided how many partitions you want? And what filesystem you wish it or them to be?

---

### Post by completeidiot on 2010-01-17
I think just one. NTFS.
That is assuming that you agree with what I have learned from this post....which can be summarized as Fat32 is essentially a dinosaur, NTFS is awesome, and NTFS will be accessible across win/lin/mac. Correct?

---

### Post by warfacegod on 2010-01-17
> **completeidiot said:**
> I think just one. NTFS.
That is assuming that you agree with what I have learned from this post....which can be summarized as Fat32 is essentially a dinosaur, NTFS is awesome, and NTFS will be accessible across win/lin/mac. Correct?

Yes, that is a reasonable assessment. Assuming you have backups then we proceed. In your first post you said that you had to partitions 1 Mac and 1 FAT32. If that is indeed the case then the next step would be to delete the other partition with Gparted.

---

### Post by completeidiot on 2010-01-17
it's an external drive that contains 1 mac, 1 fat 32. i backed up both. don't need either. want to just have the entire drive as one ntfs partition

---

### Post by theozzlives on 2010-01-17
> **completeidiot said:**
> it's an external drive that contains 1 mac, 1 fat 32. i backed up both. don't need either. want to just have the entire drive as one ntfs partition

Keep in mind Mac is read only with NTFS, but if that's not a problem, then NUKE the drive and go NTFS.

---

### Post by coldraven on 2010-01-17
Backup your files
Download and run Gparted
Make sure you select the correct drive from the drop down in the top right of the screen!
Click on the Fat32 partion image, right click, select delete.
Repeat for the Mac image.
Click on "apply changes" All your data will be lost!!!!!
Click on the "Unallocated part" ,right click select "New" , file type NTFS, give it a label so that you will find it easily.
Click "apply changes"
Within five minutes you will have a nice shiny external drive that Win/Linux can see.
For Mac use see here:

[http://applicationtidbits.com/ntfs.html](http://applicationtidbits.com/ntfs.html)
        
I presume that is correct, I do not have a Mac :D

---

### Post by completeidiot on 2010-01-17
right clicking does not give me the option to delete. but i do have the option to create new. both partitions show up and function in "documents" and all other capacities. 
?

---

### Post by completeidiot on 2010-01-17
also looks like i need to install ntfsprogs?

---

### Post by warfacegod on 2010-01-17
> **completeidiot said:**
> also looks like i need to install ntfsprogs?

Yes. I was just looking in my Synaptic to figure out which would give Gparted NTFS support.

---

### Post by warfacegod on 2010-01-17
Matter of fact, I just installed it myself.

---

### Post by warfacegod on 2010-01-17
Okay you've already deleted all of the partitions. I thought there was still one left, my fault.

Next is right click> new> in the window that appears you want to uncheck Round To Cylinders. Make sure you have it set as Primary Partition. Select NTFS from the dragdown menu, create a Label (names the drive), click create, click the green check mark.

---

### Post by completeidiot on 2010-01-17
> **warfacegod said:**
> Okay you've already deleted all of the partitions. I thought there was still one left, my fault.

Next is right click> new> in the window that appears you want to uncheck Round To Cylinders. Make sure you have it set as Primary Partition. Select NTFS from the dragdown menu, create a Label (names the drive), click create, click the green check mark.

I did not delete them...gparted is just not recognising them

---

### Post by warfacegod on 2010-01-17
> **completeidiot said:**
> I did not delete them...gparted is just not recognising them

If you already have everything backed up then go ahead and create the new partition.

---

### Post by completeidiot on 2010-01-17
ntfs is not showing up as an option here. but it is showing up as now supported on the check vs. stop sign screen that i posted the last screen shot of

---

### Post by warfacegod on 2010-01-17
> **completeidiot said:**
> ntfs is not showing up as an option here. but it is showing up as now supported on the check vs. stop sign screen that i posted the last screen shot of

Sorry for not replying sooner. Try rebooting.

---

### Post by completeidiot on 2010-01-17
Still nothing....
my options are
msdos
aix 
amiga
bsd 
dvh
gpt
mac
pc98
sun
loop
no ntfs. strange.

---

### Post by warfacegod on 2010-01-17
Check Synaptic and make sure you have the ones that have green boxes next to them.

---

### Post by completeidiot on 2010-01-17
i do. still not there

---

### Post by warfacegod on 2010-01-17
Terminal:

```
sudo apt-get purge gparted
```

```
sudo apt-get install gparted
```

---

### Post by completeidiot on 2010-01-18
still nothing despite this

---

### Post by warfacegod on 2010-01-18
When you right click the drive and select type NTFS where my pointer is, isn't selectable?

---

### Post by completeidiot on 2010-01-18
i have not gotten to a screen like that. I am prompted and asked what type of "partition table" i want to correct and ntfs is not an option
is a partition table different from a partition?

i enabled ntfs writing to external devices with ntfs-config

---

### Post by warfacegod on 2010-01-18
Apparently Gparted thinks your the partition table on your drive is damaged. Let it create the new partition table type as MS-DOS. That should stop Gparted from thinking something is broken. That then should allow you to format as NTFS.

I'm not sure why Gparted is doing that. I hunted around a bit on the net and it looks to be a pretty rare thing. Certain hardware combinations or something like that. Got waaayy too geek speak for me. I'm only fluent in Geekish.

---

### Post by completeidiot on 2010-01-18
ok. i have gotten a little further now. it does think that there is something wrong. but at least i now have the option to delete the partition.
The reason why am i doing this in the first place is because the mac partition likes to get stuck in read only....but it should be ok to delete and then create new now?

---

### Post by completeidiot on 2010-01-18
i also have the option to: Format To=> NTFS

---

### Post by completeidiot on 2010-01-18
options
should i just do the format to?
or do you think deleting and then starting with new again may let me get away from the ms-dos partition table?
also it still all shows up as one 931.51 gig partition...which means that it may not even be recognizing the fat32 partition. there have no problems with that partition so i'm not sure why it would not appear

---

### Post by warfacegod on 2010-01-18
Format as NTFS. Looks like that Mac partition really got mad about being messed with.

---

### Post by completeidiot on 2010-01-18
format to?
or do you think it would help to delete and then new?
i'm wondering what will happen to that 70 gigs if i just format to without deleting

---

### Post by warfacegod on 2010-01-18
Yeah, format to NTFS. If it goes badly (like if the Mac partition earmarked part of the drive or something) then delete and create new. From what it looks like it should be fine though.

I'm sorry this is taking so long. I'm more and more thinking that your Mac partition reacted really badly to being deleted by something that wasn't a Mac application. Windows Vista and 7 can be the same way if you resize them with Linux.

---

### Post by completeidiot on 2010-01-18
done!
although i forgot to give the drive a cool name

---

### Post by warfacegod on 2010-01-18
> **completeidiot said:**
> done!
although i forgot to give the drive a cool name

Then your name will be kjdfbkj-5u847534n.5jr78f-nvdjkfbdjfnb.s or something.

You could always format again? There's actually one more step. Back in a sec after I beat my media player over the head.

---

### Post by completeidiot on 2010-01-18
i renamed it.
what is the other step? you are making me paranoid....because i was just about to finally do my massive transfer of data back onto the drive

---

### Post by warfacegod on 2010-01-18
Paranoia? Wow.;) 

If you check the properties of the drive in a file browser you should see a difference in used space than Gparted shows. For your drive it should be around 45 GB. That's because of the system reserve. By default, Ubuntu claims 5% of a drive for itself. If you want it back then I'll need to reboot to get a Terminal command. I'll post the code in a sec.

---

### Post by completeidiot on 2010-01-18
yah, i'm only showing 929.8 gigs free
i'm assuming it's done for a good reason? 
any point in letting ubuntu have it?

---

### Post by warfacegod on 2010-01-18
```
sudo tune2fs -m x /dev/sdb
```

Replace x with the amount you want the reserve to be. If you want 3% then 3, if 25% then 25, and yes it can be 0%

---

### Post by completeidiot on 2010-01-18
i have two external and internal drive going, how do i make sure it does it to the right one?
what % would you recommend?

---

### Post by warfacegod on 2010-01-18
> **completeidiot said:**
> yah, i'm only showing 929.8 gigs free
i'm assuming it's done for a good reason? 
any point in letting ubuntu have it?

No, not on an external. Get rid of it if you like. I did two months ago, no problems.

On the drive that ubuntu is installed on, it's wise to have a reserve. If the drive is say 100 GB then 5 GB is a bit much, 2 GB would be fine. On a 20 GB drive then 5% should be left alone.

---

### Post by warfacegod on 2010-01-18
> **completeidiot said:**
> i have two external and internal drive going, how do i make sure it does it to the right one?
what % would you recommend?

I just looked at your last screen shot of Gparted. It's sdb. External 0%

---

### Post by completeidiot on 2010-01-18
tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock

---

### Post by warfacegod on 2010-01-18
```
sudo tune2fs -m x /dev/sdb
```

I can never remember if it needs to be ...../sdb or sdb1

---

### Post by completeidiot on 2010-01-18
neither seems to work
sudo tune2fs -m 0 /dev/sdb
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.
will@MyJam:~$ sudo tune2fs -m 0 /dev/sdb1
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

---

### Post by luis G on 2010-01-18
how do i post a question?? tell me please i need help with my wireless connection.

---

### Post by completeidiot on 2010-01-18
> **luis G said:**
> how do i post a question?? tell me please i need help with my wireless connection.

first search and make sure no one else has already answered and asked your question....they probably have.
if not go to beginner's talk and click new thread button above where existing threads are listed 
first i would do some searches in forums and in google. with such a basic and common problem, the answer is probably already out there

---

### Post by warfacegod on 2010-01-18
> **luis G said:**
> how do i post a question?? tell me please i need help with my wireless connection.

I suggest you go to the Networking & Wireless sub forum, in there at about the middle left of the page will be a greyish box that says New Thread, click it.

Please put as much detailed info into your post as you can.

---

### Post by warfacegod on 2010-01-18
Maybe unmount the drive?

---

### Post by completeidiot on 2010-01-18
still no luck
i think i will just give my 5% offering to the Ubuntu gods

A million thanks!!!!

---

### Post by warfacegod on 2010-01-18
The Ubuntu gods are savage and brutal aren't they? Glad to help. Don't forget to mark this thread as solved.

---

