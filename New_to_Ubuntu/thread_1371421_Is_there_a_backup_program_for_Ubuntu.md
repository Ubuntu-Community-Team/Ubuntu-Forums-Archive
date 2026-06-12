---
title: "Is there a backup program for Ubuntu?"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by oingk on 2010-01-03
Hi

I have a laptop with Windows XP and Ubuntu 9.10 dual-boot, on two partitions.

Someone in this community told me that I will probably need to backup my Ubuntu because Linux people make a new version of it every about 6 months and so I will need to reinstall my Ubuntu.

I wanted to confirm this and to ask what it actually means as I didn't understand it completely.

Also if I really have to backup Ubuntu, I would like to know if there is a special program which can do this for me by adding an extra small partition on my computer where it will save the backup. A similiar thing exists for Windows, called "Rescue and Recovery". This would save me from having to burn CDs.

Thanks

---

### Post by cjohnston on 2010-01-03
There are quite a few programs that you can use to backup your system on linux, it all depends on how you want to do your backup, and what you want to backup. As far as backing up, it will boil down to personal preference, although people on here can give you suggestions.. I use dropbox to backup my documents and such.

Yes, Ubuntu does put out a new version every 6 months; in April and October. You can either reinstall for an upgrade, or there is an option to upgrade the system without a fresh install... Once again, boils down to personal preference. Hope this helps some..

---

### Post by J V on 2010-01-03
better yet, next time you install ubuntu make a seperate partition for your /home, then you can make fresh installs but keep your data and settings, without needing to backup...

---

### Post by howefield on 2010-01-03
> **oingk said:**
> Someone in this community told me that I will probably need to backup my Ubuntu because Linux people make a new version of it every about 6 months and so I will need to reinstall my Ubuntu.

Ubuntu release a new version every 6 months, but you do not need to upgrade if what you have works for you, you do have a choice in the matter :)

The next version du next April, is an LTS version, which means it will have long term support and in that respect, it is likely that you would want to have it.

I'd always advocate a clean install when moving from one version to the next, but you can do an online upgrade just the same.

It is always a good idea to have a backup of your files in any event, never mind in preparation for an upgrade/new install.

There are several ways to do this depending on whether you want to back up your whole system, or just your own files, or specific directories. Start reading here

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)
[http://www.ubuntugeek.com/category/backup](http://www.ubuntugeek.com/category/backup)

---

### Post by oingk on 2010-01-03
In regards to backing up, I will check out "dropbox" that johnston suggested, thanks

Also I will probably want to install the April version since it will be LTS.

Since I am not so experienced and is possible that I will go through trouble when trying to make a clean install of Ubuntu, I guess I''ll go for the online upgrade.

Does this mean that I will be able to keep the data and settings of my current version of ubuntu?

---

### Post by howefield on 2010-01-03
> **oingk said:**
> Does this mean that I will be able to kep the data and settings of my current version of ubuntu?

Yes, everything should go ok and you will have your data and settings intact following your upgrade.

But note the word "should".

No one can guarantee everything will be all sweetness and light for you, it probably will, but no guarantees, hence the reason for backing up before you upgrade.

---

### Post by tea for one on 2010-01-03
Good evening

I would also recommend that you create a separate partition for your personal data.

Then I would suggest that you back up your data regularly in the event of hardware failure or other unwanted events.

Try and have a look at Grsync for backing up data - it is available via Software Centre in Karmic.

---

### Post by shuttleworthwannabe on 2010-01-03
How about backup tools? or this suggestion ([sbackup]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html"))

---

### Post by doublewitt on 2010-01-03
In GRsync, when you choose the "Switch source with destination", is that the same thing as "Restore"? Any details to how this procedure affects your data?

---

### Post by doublewitt on 2010-01-03
> **shuttleworthwannabe said:**
> How about backup tools? or this suggestion ([sbackup]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html"))
Going to give this a try...

---

### Post by doublewitt on 2010-01-03
After looking at sbackup, and seeing how it works, this is the one I will use. I've tried a few but this one seems to beat them all. It's more configurable - and it's easy to use. 

Great site - **Ubuntu Geek**...!
thanks

---

### Post by shuttleworthwannabe on 2010-01-03
Glad u came right with that. All the best.
S

---

### Post by oingk on 2010-01-04
hey thanks for the help guys I will check out the programs you recommended.
I guess I'll mark this as solved.

---

### Post by garvinrick4 on 2010-01-04
I use a free program called Clonezilla and it takes a image of whole drive not just one partition but  Windows 7, 9.10 and 10.04 and you can also take image of just 1 partition you choose. Just restore and you are back to condition of when you imaged.
 It is a live CD and not an App. 

 I sure like images a lot better than back-ups. If you do backups though make sure you
go to bookmarks in firefox then to organize bookmarks to import and backup so you can save all your bookmarks to a backup drive or flash some media or another and a copy of your home folder. Synaptic has a markings backup have copy but never tried to restore. 
 Anyone who has not made an iso of clonezilla and burned a live CD and looked through it you should it is quite nice and has an open source price. Free. Bought one of the image programs and Clonezilla is better, my mistake.

---

### Post by -kg- on 2010-01-04
[LIST]
[/LIST]

I like Clonezilla myself.  As an addendum, [here is an excellent tutorial]("http://www.dedoimedo.com/computers/free_imaging_software.html") on both Clonezilla and PartEd.

---

### Post by oingk on 2010-01-04
thanks very much.
so as I understand this clonezilla would cover both my windowsXP and my Ubuntu9.10 partitions?

---

### Post by SecretCode on 2010-01-04
Yes it would - highly recommended

---

### Post by CharlesA on 2010-01-04
> **oingk said:**
> thanks very much.
so as I understand this clonezilla would cover both my windowsXP and my Ubuntu9.10 partitions?

Yes it does.

I only image the main OS partition after doing clean installs and after getting the apps installed. For the data partition I just copy it to my server.

---

### Post by oingk on 2010-01-04
> **CharlesA said:**
> Yes it does.

I only image the main OS partition after doing clean installs and after getting the apps installed. For the data partition I just copy it to my server.


So Clonezilla is not capable of also backing up the data (files) ?

---

### Post by SecretCode on 2010-01-05
Clonezilla will copy every partition you tell it to. Even if it doesn't understand the filesystem - some future win8 format or ext5/6/7 - it will copy the raw sectors.

I think CharlesA is saying that copying the data files individually is better for him. This way you can retrieve an individual backed up file or directory, instead of having to restore the entire partition. Clonezilla is not good at that.

---

### Post by oingk on 2010-01-05
thanks v. much

---

### Post by theozzlives on 2010-01-05
I have a separate /home partition, which is the important part. I also keep a tar-ball of my /home on the network in case I "oops" during an install. In my opinion, Tar and a /home partition is all you need, just keep your tar-ball up to date.

---

### Post by oingk on 2010-01-05
> **theozzlives said:**
> I have a separate /home partition, which is the important part. I also keep a tar-ball of my /home on the network in case I "oops" during an install. In my opinion, Tar and a /home partition is all you need, just keep your tar-ball up to date.


What is a /home partition?
Also what is a tar-ball?

---

