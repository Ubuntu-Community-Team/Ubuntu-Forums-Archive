---
title: "Hard Drive dead..."
date: 2008-12-24
forum: New to Ubuntu
---

### Post by GateKeeping on 2008-12-24
After experiencing trouble booting Window's XP I installed Ubuntu in hopes to gain a look at my hard drive.

Upon clicking on Places/Computer I see the CD/DVD drive, Filesystem, and another drive S3A3050D002 which when I right click I am shown it's empty.

Looks like I might have formatted my hard drive by mistake. Is there anyway of knowing if any data is still on my hard drive?

Thanks!

Patrick

---

### Post by albinootje on 2008-12-24
> **GateKeeping said:**
> After experiencing trouble booting Window's XP I installed Ubuntu in hopes to gain a look at my hard drive.

Upon clicking on Places/Computer I see the CD/DVD drive, Filesystem, and another drive S3A3050D002 which when I right click I am shown it's empty.

Looks like I might have formatted my hard drive by mistake. Is there anyway of knowing if any data is still on my hard drive?


Try testdisk.
You can perform this in a "live session" from the Ubuntu installation cdrom in a terminal :
```

sudo apt-get install testdisk
sudo testdisk

```
Read the documentation here :
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by balaknair on 2008-12-24
There's a little tool called test-disk, which can recover data from damaged or accidentally formatted drives.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Install using the following command in a terminal(Applications menu> Accessories> Terminal)

*sudo apt-get install testdisk*

---

### Post by GateKeeping on 2008-12-24
> **balaknair said:**
> There's a little tool called test-disk, which can recover data from damaged or accidentally formatted drives.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Install using the following command in a terminal(Applications menu> Accessories> Terminal)

*sudo apt-get install testdisk*

I don't have Ubuntu installed on my laptop -yet! I just downloaded it and burned it to a CD and now running the TRY IT from the burned CD I made so I don't have TestDisk. 

I downloaded testdisk-6.10-1.i386.rpm (not even sure if that's the version I need) but still I saved it to a flash drive, because I can't use the CD-Rom right now since I'm using the CD ROM to operate Ubuntu's TRY It first version. 

What is the "sudo get-apt" prompt that I must use to get the testdisk-6.10-1.i386.rpm from my flash drive?

Patrick

---

### Post by albinootje on 2008-12-24
> **GateKeeping said:**
> I don't have Ubuntu installed on my laptop -yet!

You can run a "live sesssion" with the Ubuntu installation cdroms.
And within that "live session" you can install software! It will stay in RAM memory for as long as you use that "live session".
> 
 I just downloaded it and burned it to a CD and now running the TRY IT from the burned CD I made so I don't have TestDisk. 

I downloaded testdisk-6.10-1.i386.rpm (not even sure if that's the version I need) but still I saved it to a flash drive, because I can't use the CD-Rom right now since I'm using the CD ROM to operate Ubuntu's TRY It first version. 

What is the "sudo get-apt" prompt that I must use to get the testdisk-6.10-1.i386.rpm from my flash drive?

Forget about the testdisk-6.10-1.i386.rpm, that's meant for rpm-based Linux distributions like Fedora and OpenSUSE.

If you have internet connection while using the Ubuntu installation cdrom, you can just do the "sudo apt-get install testdisk".

---

### Post by GateKeeping on 2008-12-26
> **albinootje said:**
> 

If you have internet connection while using the Ubuntu installation cdrom, you can just do the "sudo apt-get install testdisk".

I tried running "sudo apt-get install testdisk" but still no luck. It seems to be looking for it on the CD but can not find it.

What should I do?

Thanks!

Patrick

---

### Post by albinootje on 2008-12-26
> **GateKeeping said:**
> I tried running "sudo apt-get install testdisk" but still no luck. It seems to be looking for it on the CD but can not find it. 

You have the Ubuntu installation cdrom in the drive ?

testdisk is in "Universe", I don't know whether that's included on the cdroms.

Can you download and install it from here instead ?
[http://packages.ubuntu.com/search?keywords=testdisk](http://packages.ubuntu.com/search?keywords=testdisk)

---

### Post by dwasifar on 2008-12-26
In addition to testdisk, you might also try looking at your disk in the partition editor.  System > Administration > Partition Editor.  This will tell you if the drive is reporting any Windows partitions (FAT32 or NTFS).  If your drive has actually failed it will probably not report any partitions at all.

---

### Post by -kg- on 2008-12-26
> After experiencing trouble booting Window's XP I installed Ubuntu in hopes to gain a look at my hard drive.

Looks like I might have formatted my hard drive by mistake. Is there anyway of knowing if any data is still on my hard drive?

> In addition to testdisk, you might also try looking at your disk in the partition editor. System > Administration > Partition Editor. This will tell you if the drive is reporting any Windows partitions (FAT32 or NTFS). If your drive has actually failed it will probably not report any partitions at all.

Not only that, but if it hasn't failed GPartEd will tell you whether and how much is contained in that (or all) partitions.  If you have accidentally formatted your entire partition (not hard drive...if you had formatted your entire hard drive, there would be nothing but your Ubuntu partitions with no Windows partition at all) you will show a very low number under the "Used" column in the partition list in the editor.

See [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") for a good explanation of what partitioning is and does.

---

### Post by GateKeeping on 2008-12-27
> **-kg- said:**
> Not only that, but if it hasn't failed GPartEd will tell you whether and how much is contained in that (or all) partitions.  If you have accidentally formatted your entire partition (not hard drive...if you had formatted your entire hard drive, there would be nothing but your Ubuntu partitions with no Windows partition at all) you will show a very low number under the "Used" column in the partition list in the editor.

See [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") for a good explanation of what partitioning is and does.

The Partition Manager is showing /dev/sda1/ ntfs size 92.97 GiB and nothing else. The hard drive appears to be working fine, but I can't locate anything on it.

---

### Post by -kg- on 2008-12-27
> The Partition Manager is showing /dev/sda1/ ntfs size 92.97 GiB and nothing else. The hard drive appears to be working fine, but I can't locate anything on it.

OK, below is a screenshot of GParted:

[IMG]http://i363.photobucket.com/albums/oo77/ubun3uc/ExtPartCreated.png[/IMG]

Notice the "Used" and "Unused" columns?  You notice that the 1st Primary partition in the screenshot (the one I have actually created...the others in the screenshot are yet to be created) has a "Used" value of 65.35 MB and the "Unused' column indicates 29.08 GB.  This partition has no files on it (I created it for demonstration purposes for the "How To Partition" page) and the 65.35 MB is a low value and is the overhead of the partition.

When you view your partition in GPartEd you should see a similar view.  If there are files contained in your partition the "Used" value should be significantly higher...several GB for an XP installation.  You should also be able to see a "Yellow" portion on the left side of the graphic bar which would indicate there are files present.

Tell us what you find out.  If you can, post a screenshot of your GPartEd window.

---

### Post by GateKeeping on 2008-12-27
> **-kg- said:**
> OK, below is a screenshot of GParted:

[IMG]http://i363.photobucket.com/albums/oo77/ubun3uc/ExtPartCreated.png[/IMG]

Notice the "Used" and "Unused" columns?  You notice that the 1st Primary partition in the screenshot (the one I have actually created...the others in the screenshot are yet to be created) has a "Used" value of 65.35 MB and the "Unused' column indicates 29.08 GB.  This partition has no files on it (I created it for demonstration purposes for the "How To Partition" page) and the 65.35 MB is a low value and is the overhead of the partition.

When you view your partition in GPartEd you should see a similar view.  If there are files contained in your partition the "Used" value should be significantly higher...several GB for an XP installation.  You should also be able to see a "Yellow" portion on the left side of the graphic bar which would indicate there are files present.

Tell us what you find out.  If you can, post a screenshot of your GPartEd window.

Here's a screenshot of mine:

[IMG]http://i462.photobucket.com/albums/qq346/iBringSolutions/Screenshot--dev-sda-GParted.png[/IMG]

If I can find out what is left on my hard drive then I can decide what to do next.

If my hard drive was in fact formatted is there any known way to recover anything from it?

I very much appreciate your help. 

Patrick

---

### Post by -kg- on 2008-12-28
OK, from your screenshot, I see that there are 3 GB worth of files in your NTFS partition, so there are definitely files there.  Seemingly a small amount for an XP installation, but there are files there. Notice also the "yellow" portion on the graphical bar that I mentioned earlier.

OK, click the "Places" menu on the top launch bar from the Live CD desktop(which will be Nautilus), then click "Computer."  This will launch Nautilus with a view of the entire hard drive and all the partitions and CD-ROM (called drives) on the computer.

Right click on the Windows drive and select "Mount" from the menu, then click on it so that you can view what is on that drive.  You _should_ be able to view the files present on that partition.

See if you have any luck with this.  The files are there (and shown to be there by GPartEd), so you should be able to see them using this method.

---

### Post by GateKeeping on 2008-12-29
> **-kg- said:**
> OK, from your screenshot, I see that there are 3 GB worth of files in your NTFS partition, so there are definitely files there.  Seemingly a small amount for an XP installation, but there are files there. Notice also the "yellow" portion on the graphical bar that I mentioned earlier.

OK, click the "Places" menu on the top launch bar from the Live CD desktop(which will be Nautilus), then click "Computer."  This will launch Nautilus with a view of the entire hard drive and all the partitions and CD-ROM (called drives) on the computer.

Right click on the Windows drive and select "Mount" from the menu, then click on it so that you can view what is on that drive.  You _should_ be able to view the files present on that partition.

See if you have any luck with this.  The files are there (and shown to be there by GPartEd), so you should be able to see them using this method.


I got as far as you indicated, could see folders I recognize like Documents and Settings, but all the folders are empty. I guess that's the reason why the 'used' 3Gig portion is so small.

Seems like the drive has in fact been formatted and all the data is lost. Unless there's a known way to recover files from a formatted HD I'll have to bite the bullet and say good bye to all the data that was there.

Thanks for you help.

Patrick

---

### Post by -kg- on 2008-12-31
> I got as far as you indicated, could see folders I recognize like Documents and Settings, but all the folders are empty. I guess that's the reason why the 'used' 3Gig portion is so small.

Seems like the drive has in fact been formatted and all the data is lost. Unless there's a known way to recover files from a formatted HD I'll have to bite the bullet and say good bye to all the data that was there.

Most peculiar.  If the partition had been reformatted, there would have been nothing there at all to see.  If all the folders on that partition had been empty, there would have been far less than 3 GB of data on the partition.  Empty folders take up almost no room at all.  All a folder is is a sub-directory entry.

I think next you might want to go back in to where you saw your folders, right click on those folders, and select "Properties" from the menu.  2nd line from the top is "Contents:" which will show you how many "items" are in the folder and how much disk space is used by these items.  Items will include anything in the folder and it's sub-folders.

A truly empty folder will show 0 items at 0 bytes.  If there are empty sub-folders contained within the folder, it will show the sub-folders as # (number of) items, but it will still show it to be at 0 bytes.  If you right click on a folder and it shows anything other than 0 bytes, there are files in that folder (or one of it's sub-folders, whether you can see them or not (though I don't know why you wouldn't be able to see them).

I got this information looking at my Vista installation on this computer.  In order to get the information on properties of folders and sub-folders, I created a test folder, created another test folder within that folder, then created another one under that sub-folder.  When I pulled the properties on the top level folder, it showed 2 items at 0 bytes.

Now ***THAT*** is interesting!  I just looked in *MY* Documents and Settings.  I *KNOW* that I have files in my Documents and Settings file, yet I show that there is *NOTHING!*

I am going to reboot into Vista after I finish this and check, but if this is true and I can't view the files under Documents and Settings, but they are indeed there when I check under Vista, I wouldn't be *too* sure that your files are indeed gone.

Let me go check this...

---

### Post by GateKeeping on 2009-01-01
> **-kg- said:**
> Most peculiar.  If the partition had been reformatted, there would have been nothing there at all to see.  If all the folders on that partition had been empty, there would have been far less than 3 GB of data on the partition.  Empty folders take up almost no room at all.  All a folder is is a sub-directory entry.

I think next you might want to go back in to where you saw your folders, right click on those folders, and select "Properties" from the menu.  2nd line from the top is "Contents:" which will show you how many "items" are in the folder and how much disk space is used by these items.  Items will include anything in the folder and it's sub-folders.

A truly empty folder will show 0 items at 0 bytes.  If there are empty sub-folders contained within the folder, it will show the sub-folders as # (number of) items, but it will still show it to be at 0 bytes.  If you right click on a folder and it shows anything other than 0 bytes, there are files in that folder (or one of it's sub-folders, whether you can see them or not (though I don't know why you wouldn't be able to see them).

I got this information looking at my Vista installation on this computer.  In order to get the information on properties of folders and sub-folders, I created a test folder, created another test folder within that folder, then created another one under that sub-folder.  When I pulled the properties on the top level folder, it showed 2 items at 0 bytes.

Now ***THAT*** is interesting!  I just looked in *MY* Documents and Settings.  I *KNOW* that I have files in my Documents and Settings file, yet I show that there is *NOTHING!*

I am going to reboot into Vista after I finish this and check, but if this is true and I can't view the files under Documents and Settings, but they are indeed there when I check under Vista, I wouldn't be *too* sure that your files are indeed gone.

Let me go check this...

Much appreciate your effort.

At some point while trying to fix things I fiddled around with XP's recovery CD and inadvertently started re-installing XP. When I realized what was happening I panicked and shut down the computer. :( Not a good thing I know, but it was too late.

Seeing the usual My Documents folder, etc, I'm thinking that maybe the folders I'm currently seeing are part of the new XP install.

I want to be 100% sure the harddrive has nothing on it before I decide to format and re-install XP.

Cheers!

---

### Post by -kg- on 2009-01-01
Well, curiouser and curiouser.

I checked in Vista, and there was no "Documents and Settings" folder displayed.  I finally found it when I set the Folders Options to "Display Hidden Folders," and it would not let me view the contents of the folder, no matter what I did.  I suppose it's a peculiarity of Vista.

Anyway, I know that XP has that folder and it is not hidden, so I can't understand why you can't view it's contents.  Have you tried viewing the contents of any other folders on that partition?

There's obviously something on that partition, so you should be able to find *something.*

---

### Post by Delever on 2009-01-01
Vista uses C:\Users\<user name>\Documents

---

### Post by -kg- on 2009-01-01
> Much appreciate your effort.

At some point while trying to fix things I fiddled around with XP's recovery CD and inadvertently started re-installing XP. When I realized what was happening I panicked and shut down the computer. Not a good thing I know, but it was too late.

Seeing the usual My Documents folder, etc, I'm thinking that maybe the folders I'm currently seeing are part of the new XP install.

I want to be 100% sure the harddrive has nothing on it before I decide to format and re-install XP.

Mercy!  Well, all I can tell you is to look in all the folders contained on your partition, and see if there is anything you can recover.  You might have some of your data still there, and might be able to recover it, though shutting down the computer in mid-reinstall/repair...I don't know.

Definitely, let me know what you find.  Windows is ***such a PITA*** that I would love to leave it all behind...**_ALL OF IT!_**

I sometimes wish I had never had the experience!

---

### Post by GateKeeping on 2009-01-01
> **-kg- said:**
> 
Windows is ***such a PITA*** that I would love to leave it all behind...**_ALL OF IT!_**

I sometimes wish I had never had the experience!

I second that thought!

As for the folders and the data they contain they are definitely from the re-install/repair. I recognize the Toshiba files. 

But even though only a handful of folders and files 'seem' to be there, something tells me that someone with much more knowledge on the matter than me might be able to find the old data still on the hard drive. Because although some of the folders from the re-install did have time to install before I shut everything down, I'm almost certain the re-install never had enough time to reformat the HD. So something tells the data is still there.

Thanks for all your help and happy new year!

---

### Post by GateKeeping on 2009-01-27
Just wanted to thank everyone here who helped me get through the rough patches when my hard drive died.

All is well again.

Thank you!

Patrick

---

