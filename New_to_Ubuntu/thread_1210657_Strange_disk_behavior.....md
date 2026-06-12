---
title: "Strange disk behavior...."
date: 2009-07-11
forum: New to Ubuntu
---

### Post by towoha on 2009-07-11
Hi.
I have a HD that I only can read it's contents on a Linux computer. It's files and folders are created on a Win computer, but when I put the disk in a Win computer now, it don't even show up in "My computer" Any ideas out there?

---

### Post by LewRockwell on 2009-07-11
you might run Testdisk on it, Parted Magic has Testdisk on it or you can get it other places as well

[http://www.partedmagic.com/](http://www.partedmagic.com/)

.

---

### Post by towoha on 2009-07-12
And do what with it? I need the disk to work under Windows, not only Linux... 
Any other ideas?

---

### Post by Penguin Guy on 2009-07-12
What format are the partition(s) on it? I believe that Windows can only read fat partitions.

---

### Post by towoha on 2009-07-12
> **Penguin Guy said:**
> What format are the partition(s) on it? I believe that Windows can only read fat partitions.

It's a NTFS and it's been formated in Windows. Win reads NTFS and FAT.

---

### Post by halitech on 2009-07-12
does the drive show up in the bios when you install the drive in the windows computer?

---

### Post by towoha on 2009-07-12
> **halitech said:**
> does the drive show up in the bios when you install the drive in the windows computer?

Jepp. If I install it into my computer it comes up under the bios.

---

### Post by halitech on 2009-07-12
I would suggest putting the drive back into the linux computer and then post the output of
```
sudo fdisk -l
```thats a lower case L, not the number 1

---

### Post by FoxFireX on 2009-07-12
For the love of god, Boot into windows and go to start -> run and type in "diskmgmt.msc" look for the drive right click it and assign it a drive letter.

done.

---

### Post by towoha on 2009-07-12
> **FoxFireX said:**
> For the love of god, Boot into windows and go to start -> run and type in "diskmgmt.msc" look for the drive right click it and assign it a drive letter.

done.

I can't do that. The only option I get is: Delete this partition...

---

### Post by towoha on 2009-07-12
> **halitech said:**
> I would suggest putting the drive back into the linux computer and then post the output of
```
sudo fdisk -l
```thats a lower case L, not the number 1

fdisk doesn't work =( I have a Aces Aspire One with Linux4One (Ubunt distro) So I can only connect the disk through a external IDE cabinett I have with usb.

---

### Post by halitech on 2009-07-12
with it connected through USB it should still see the drive

---

### Post by northern lights on 2009-07-12
> **towoha said:**
> fdisk doesn't work =( I have a Aces Aspire One with Linux4One (Ubunt distro) So I can only connect the disk through a external IDE cabinett I have with usb.

If external harddrives are properly recognized by your Linux OS, *fdisk -l* will list them just like internal ones. Have you guessed it won't show, or tried it?

---

### Post by towoha on 2009-07-12
> **northern lights said:**
> If external harddrives are properly recognized by your Linux OS, *fdisk -l* will list them just like internal ones. Have you guessed it won't show, or tried it?

I have tried it a number of times now and I get no output with fdisk -l command.

---

### Post by towoha on 2009-07-12
But now i ran it with sudo: e.g: sudo fdisk -l and this was the output:

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d0272

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98b75309

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux

---

### Post by LewRockwell on 2009-07-12
> **towoha said:**
> And do what with it? I need the disk to work under Windows, not only Linux... 
Any other ideas?

[http://download.cnet.com/TestDisk-PhotoRec/3000-2248_4-10511775.html](http://download.cnet.com/TestDisk-PhotoRec/3000-2248_4-10511775.html)

gasoline...

matches...

let's roll!

.

---

### Post by halitech on 2009-07-12
if this [color="red"]/dev/sdb1 1 36481 293033601 83 Linux[/color] is the external drive then its been formatted by linux. If its EXT3, you could try grabbing a copy of an ext2/3 reader for windows but that will only allow you to read the drive, if you need it to write from windows as well, back it up and format NTFS so both can read and write to it.

---

### Post by LewRockwell on 2009-07-12
> **towoha said:**
> But now i ran it with sudo: e.g: sudo fdisk -l and this was the output:

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d0272

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7494291   83  Linux
/dev/sda2             934         981      385560    5  Extended
/dev/sda5             934         981      385528+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98b75309

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux

with reference to your findings(quoted above) via the sudo fdisk -l...

you have absolutely no file system(s) indicating ANY windows data exists

.

---

### Post by LewRockwell on 2009-07-12
if you would like to rescue/retrieve windows data on that hard drive you will want to utilize Testdisk and possibly Photorec

.

---

### Post by theozzlives on 2009-07-12
If it's read only, I'd say copy all the files off it and re-partition/format. Linux can read and WRITE NTFS, and an FS driver will allow Windows to read and WRITE to an ext3. Besides if it was ext3, Windows would see it in Disk Manager and call it "unknown".

---

### Post by Skrean on 2009-07-12
Please do what Halitech suggested above so that we may help.

---

### Post by towoha on 2009-07-12
Well, this disk doesn't say what format it is... 
[I]Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98b75309[/I]

And that's the disk I'm having the problem with. Is there any way I can find out what format it's in now? Has it just lost it's formatation? What can have happened?

---

### Post by halitech on 2009-07-12
> **towoha said:**
> Well, this disk doesn't say what format it is... 
[I]Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98b75309[/I]

And that's the disk I'm having the problem with. Is there any way I can find out what format it's in now? Has it just lost it's formatation? What can have happened?

that is the drive, this is the partition on the drive

```

Device Boot Start End Blocks Id System
/dev/sdb1 1 36481 293033601 83 Linux
```

It's been formated by Linux and you either need to get a driver to allow windows to read ext3 or you need to format it in NTFS/FAT32 so both can see it.

---

### Post by towoha on 2009-07-12
> **halitech said:**
> that is the drive, this is the partition on the drive

```

Device Boot Start End Blocks Id System
/dev/sdb1 1 36481 293033601 83 Linux
```

It's been formated by Linux and you either need to get a driver to allow windows to read ext3 or you need to format it in NTFS/FAT32 so both can see it.

But if I format it to ntfs/fat32 I will loose all my data, and that simply can not happen!

---

### Post by halitech on 2009-07-12
then you need to get a driver to allow windows to see ext3 partitions

---

### Post by LewRockwell on 2009-07-12
> **towoha said:**
> Well, this disk doesn't say what format it is... 
[I]Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98b75309[/I]

And that's the disk I'm having the problem with. Is there any way I can find out what format it's in now? Has it just lost it's formatation? What can have happened?

the drive was somehow reformatted to Linux

the data on the drive has not been erased or written over YET

if you want to recover it(if possible) you will need to run the recovery software

otherwise...and in reference to your original observation...

of course windows doesn't see anything...it's formatted for linux...

Wheeee, look at the electrons go!

.

---

### Post by LewRockwell on 2009-07-12
> **halitech said:**
> then you need to get a driver to allow windows to see ext3 partitions

no...No...NO DAMMIT...

OP has a bunch of windoze data on a drive that has now somehow been reformatted to linux...

if windows could see ext3 data why would that matter in this case?

it was WINDOWS that wrote the data to either ntfs or fat or fat32 or even W95...

if OP wants to attempt to recover OP's data then OP will need to use recovery software(Testdisk and possibly Photorec)

Wheeeeee.....

.

---

### Post by towoha on 2009-07-12
Ok, I have now tried out the: DiskInternals Linux Reader. It finds the disk but I get errormessage: Filesystem is not supproted. I the read the properties of the disk and it says it's a Linux native file system, with mbr partition?? 

Printscreen here: 
[http://image55.webshots.com/555/9/59/51/2995959510102750835PXryat_fs.jpg](http://image55.webshots.com/555/9/59/51/2995959510102750835PXryat_fs.jpg)

---

### Post by halitech on 2009-07-12
depending on what they have done with the drive since it was formated it may not matter but he can try testdisk (probably the better option) but by the sounds of it, even if he can see the files, he doesn't have room to save them on his other drive so unless testdisk can unformat the drive to ntfs/fat32 it may not make much difference.

I'll admit I've never had to use testdisk so I dont know exactly how it handles recovery so if you know Lew, perhaps writting things out will help the OP alot.

---

### Post by LewRockwell on 2009-07-12
When I get PAID to do data recovery, the first thing I do is boot up a *nix LiveCD and see if I can see, copy, and recover the data

That takes a few minutes and is much more sensible and efficient that just assuming that Testdisk is the only way out

(the reason I mentioned it at the beginning of this thread is because the OP made note that the data was visible(accessible? maybe/maybe-not) with Linux and so if they could copy the data via Ubuntu...then why not rescue/recover it with Ubuntu instead of attempting to make it viewable once again in windoze?)

.

---

### Post by jerome1232 on 2009-07-12
> **LewRockwell said:**
> 

if OP wants to attempt to recover OP's data then OP will need to use recovery software(Testdisk and possibly Photorec)

Wheeeeee.....

.

As LewRockwell so eloquently put, That partition was formated to a linux filesystem, erasing any data you had on their previously.

What you need to do is 

A: Use testdisk (don't know if it can rescue partitions after a format) or

B: Use photorec to recover data via file carving.

Here is a link about data recovery with some useful tips.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


Judging by your partitions you let Ubuntu have the whole hard drive and got rid of Windows as well, was this your intention?

---

### Post by LewRockwell on 2009-07-12
> **halitech said:**
> I'll admit I've never had to use testdisk so I dont know exactly how it handles recovery so if you know Lew, perhaps writting things out will help the OP alot.

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

---

### Post by towoha on 2009-07-12
Now I have also tried out the TestDisk aostware, and I can't say I'm getting anywhere with that either =( 
Here's a printscreen of it. (Sorry about the corruptet colours!)
[http://image74.webshots.com/174/2/72/48/2834272480102750835KNdbIm_fs.jpg](http://image74.webshots.com/174/2/72/48/2834272480102750835KNdbIm_fs.jpg)

---

### Post by towoha on 2009-07-12
> **halitech said:**
> depending on what they have done with the drive since it was formated it may not matter but he can try testdisk (probably the better option) but by the sounds of it, even if he can see the files, he doesn't have room to save them on his other drive so unless testdisk can unformat the drive to ntfs/fat32 it may not make much difference.

I'll admit I've never had to use testdisk so I dont know exactly how it handles recovery so if you know Lew, perhaps writting things out will help the OP alot.

I have enough other disk to stick into my computers ;) So I have noe storage problem, just a read and copy problem from the corupted disk...

---

### Post by towoha on 2009-07-12
> **LewRockwell said:**
> When I get PAID to do data recovery, the first thing I do is boot up a *nix LiveCD and see if I can see, copy, and recover the data

That takes a few minutes and is much more sensible and efficient that just assuming that Testdisk is the only way out

(the reason I mentioned it at the beginning of this thread is because the OP made note that the data was visible(accessible? maybe/maybe-not) with Linux and so if they could copy the data via Ubuntu...then why not rescue/recover it with Ubuntu instead of attempting to make it viewable once again in windoze?)

.

I agree with you here :-) But I don't have any more portable disks with usb access... But *NIX LiveCD, what's that???

---

### Post by LewRockwell on 2009-07-12
Formatting 101

Formatting sets the disk up to be used in a certain fashion(respective of file system).

The act of formatting DOES NOT delete or erase data off of the drive(other than perhaps rewriting the master boot record and the partition tables and such)

It's ALMOST ALWAYS still there...at least until somebody starts actively writing over it...


Secure Erase 101

It should also be noted that the same thing happens when "deleting" or "erasing" data(raw data, files, folders, etc.)

None of it is actually rendered unreadable/unrecoverable/undeletable/unerasable

UNLESS it's been securely erased INTENTIONALLY through some piece of software and through being WRITTEN-OVER

some operating systems offer this function as an option selectable in their standard package offerings

.

---

### Post by halitech on 2009-07-12
> **LewRockwell said:**
> [http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

interesting read, now here's hoping I never have to use it :)

---

### Post by LewRockwell on 2009-07-12
> **towoha said:**
> I agree with you here :-) But I don't have any more portable disks with usb access... But *NIX LiveCD, what's that???

*nix is just a "catch-all" way of saying unix/linux systems

the reason I don't use Ubuntu LiveCD is that it's too heavy and bloated

takes too long to load and then it's pretty heavy-handed with permission limitations

(of course, by the same standard, other distros just hand you root and say "go for it" "hack away")

as far as testdisk goes, there is a learning curve(as with anything)

I don't think your situation is a lost cause til you actually start writing over your old data

.

---

### Post by towoha on 2009-07-12
> **LewRockwell said:**
> *nix is just a "catch-all" way of saying unix/linux systems

the reason I don't use Ubuntu LiveCD is that it's too heavy and bloated

takes too long to load and then it's pretty heavy-handed with permission limitations

(of course, by the same standard, other distros just hand you root and say "go for it" "hack away")

as far as testdisk goes, there is a learning curve(as with anything)

I don't think your situation is a lost cause til you actually start writing over your old data

.

Ok, now I get it. I should downlaod a *nix live cd (a lite version of a small and easy driven os) and then read the disk in livecd, and then copy my files over to a stable disk. Than I can remount the disk in Win, and formate it. Without having the risk of destroying data... 
Correct? 
But why can't I get the files from Win now? There must be a way to read and copy the files on the disk, other then using TestDisk. I find it wery difficult to use :-(

---

### Post by jerome1232 on 2009-07-12
Wait 2 seconds here, are you saying your CAN currently access these files under Linux?

---

### Post by towoha on 2009-07-12
> **jerome1232 said:**
> Wait 2 seconds here, are you saying your CAN currently access these files under Linux?

Jupp, Can access them under Linux, but not under Windows. I was hoping there's a way I can access them with the disk mounted in Win, but it seems hopeless :-(

---

### Post by LewRockwell on 2009-07-12
> **towoha said:**
> Ok, now I get it. I should downlaod a *nix live cd (a lite version of a small and easy driven os) and then read the disk in livecd, and then copy my files over to a stable disk. Than I can remount the disk in Win, and formate it. Without having the risk of destroying data... 
Correct? 
But why can't I get the files from Win now? There must be a way to read and copy the files on the disk, other then using TestDisk. I find it wery difficult to use :-(

Testdisk and Photorec(and other recovery software utilities as well) "find" all the files that were created and indexed...but somehow were "discarded" via some event(in your case, reformatting)

While formatted and utilized with a specific file system, data is "cataloged" and easily "findable" on the storage media...when the media is reformatted the "catalog" is deleted and then the data is not "findable" in the same manner as when the "catalog" still exists

What recovery software does is search the drive for the actual data(without "needing" to look at a "catalog" like the "standard" operating systems do) and then reporting back to the user...what it has found...

It may be a very time-consuming process and the recovery software may need to run for hours or in some cases of large devices with hundreds of thousands of individual files...it may take days...

After further rereading and consideration of your specific situation I'm inclined to believe that your ONLY hope is a recovery utility

In the Testdisk screenshot you provided it is just showing the linux partition that we can already see with a *nix distro(including ubuntu)

*******************

Look, I'll give it to you straight-up...

If you want the stuff off that drive you're going to be required to either work at it...or pay for it...

You MUST read this page and follow the linked reading also
([http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk))

You've got several choices:

You can just go on and not worry about losing it

You can pay someone to recover it for you(and pay again if it happens again)

Or you can learn and do it yourself thereby saving money and gaining valuable knowledge along the way that can help you and your friends in the future

*************************

back-up...Back-up...BACK-UP your data folks...right now...before it's too late...

there are hundreds of articles, forums, and posts related to back-ups, clones, and static data long-term storage options!

.

---

### Post by LewRockwell on 2009-07-12
> **towoha said:**
> Jupp, Can access them under Linux, but not under Windows. I was hoping there's a way I can access them with the disk mounted in Win, but it seems hopeless :-(

what do you actually see in Linux?

do you actually see individual files?

if you can see what you want to save then that is GREAT!

then, if you can do that, you can download, burn, and run Puppy Linux LiveCD to copy those files somewhere safe

.

---

### Post by halitech on 2009-07-12
> **towoha said:**
> Jupp, Can access them under Linux, but not under Windows. I was hoping there's a way I can access them with the disk mounted in Win, but it seems hopeless :-(

you just need a program for Windows to be able to "see" the data on the ext3 drive such as Ext2fs

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

there is *NO* recovery needed if you can see the data in Ubuntu, just need to either show windows how to see it (with something like Ext2fs) or get the data off and format it in something both *nix and Windows can see.

---

### Post by LewRockwell on 2009-07-12
the reason I use Puppy instead of Ubuntu is that the Ubuntu permissions are a hassle when you're just trying to get stuff done...

.

---

### Post by jerome1232 on 2009-07-12
> **towoha said:**
> Jupp, Can access them under Linux, but not under Windows. I was hoping there's a way I can access them with the disk mounted in Win, but it seems hopeless :-(

If it's formated as ext3, you just need an ext2/3 driver that supportes 256 byte inodes, if it is ext4 then you can't use it from Windows. 

Here is a link to one that will work if the drive is ext3 [http://ext2fsd.sourceforge.net/](http://ext2fsd.sourceforge.net/)


In case it's ext4 you said you have more drives right? You could just copy that data to another disk that is ntfs, or copy the data to any location, format the drive as ntfs and copy the data back.

---

### Post by towoha on 2009-07-12
> **LewRockwell said:**
> Testdisk and Photorec(and other recovery software utilities as well) "find" all the files that were created and indexed...but somehow were "discarded" via some event(in your case, reformatting)

While formatted and utilized with a specific file system, data is "cataloged" and easily "findable" on the storage media...when the media is reformatted the "catalog" is deleted and then the data is not "findable" in the same manner as when the "catalog" still exists

What recovery software does is search the drive for the actual data(without "needing" to look at a "catalog" like the "standard" operating systems do) and then reporting back to the user...what it has found...

It may be a very time-consuming process and the recovery software may need to run for hours or in some cases of large devices with hundreds of thousands of individual files...it may take days...

After further rereading and consideration of your specific situation I'm inclined to believe that your ONLY hope is a recovery utility

In the Testdisk screenshot you provided it is just showing the linux partition that we can already see with a *nix distro(including ubuntu)

*******************

Look, I'll give it to you straight-up...

If you want the stuff off that drive you're going to be required to either work at it...or pay for it...

You MUST read this page and follow the linked reading also
([http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk))

You've got several choices:

You can just go on and not worry about losing it

You can pay someone to recover it for you(and pay again if it happens again)

Or you can learn and do it yourself thereby saving money and gaining valuable knowledge along the way that can help you and your friends in the future

*************************

back-up...Back-up...BACK-UP your data folks...right now...before it's too late...

there are hundreds of articles, forums, and posts related to back-ups, clones, and static data long-term storage options!

.

Ok. I will learn to do it my self :-) I don't want to pay large amount of money to rescue private data. 

Well it was my backup this one, and I was shure it was NTFS format, I've NEVER reformated it to any Linux format! But from now on I'm taking a backup of the backup!!! This is cousing to much of pain and work...

---

### Post by towoha on 2009-07-12
> **LewRockwell said:**
> what do you actually see in Linux?

do you actually see individual files?

if you can see what you want to save then that is GREAT!

then, if you can do that, you can download, burn, and run Puppy Linux LiveCD to copy those files somewhere safe

.

Yes, on my Linux machine I can se, copy, edit, and save each indiviual file, just as it was a normal disk runing on any OS. I think that's the solution for me now. I will try downloading the Puppy Linux (don't know how it works, but I think I can manage it)

---

### Post by towoha on 2009-07-12
> **halitech said:**
> you just need a program for Windows to be able to "see" the data on the ext3 drive such as Ext2fs

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

there is *NO* recovery needed if you can see the data in Ubuntu, just need to either show windows how to see it (with something like Ext2fs) or get the data off and format it in something both *nix and Windows can see.

As I posted earlier i tried the Linux reader, but that can't access the disk in Windows. Maby that's an inicator that the disk is an EXT4 format?

---

### Post by jerome1232 on 2009-07-12
Easy way to find out is if you open a terminal and type this command.

```
mount | grep /dev/sdb1
```

what that does exactly


**mount** prints a listing of all mounted devices, their filesystem type and etc...

** | ** This is known as a pipe, it just sends the information that would've been printed to the screen into another program (in our case grep)

**grep /dev/sdb1** This searches through text for lines that contain /dev/sdb1 and prints them out to the screen

---

### Post by towoha on 2009-07-12
> **towoha said:**
> As I posted earlier i tried the Linux reader, but that can't access the disk in Windows. Maby that's an inicator that the disk is an EXT4 format?

I now used the: EXT volume manager and there it says it's EXT3 file system. But I can't change the drive letter ore access the disk. What am I doing wrong in the program?
Here's a PrtScn:
[http://image96.webshots.com/96/4/96/17/2638496170102750835KDKeaj_fs.jpg](http://image96.webshots.com/96/4/96/17/2638496170102750835KDKeaj_fs.jpg)

---

### Post by jerome1232 on 2009-07-12
I get

Forbidden

You don't have permission to access /96/4/96/17/2638496170102750835KDKeaj_fs.jpg on this server.



Just use the manage attachments button to attach the picture.

---

### Post by towoha on 2009-07-12
[[IMG]http://thumb15.webshots.net/t/96/96/4/96/17/2638496170102750835KDKeaj_th.jpg[/IMG]](http://good-times.webshots.com/photo/2638496170102750835KDKeaj)

---

### Post by towoha on 2009-07-12
*now downloading puppy*

---

### Post by towoha on 2009-07-12
I have now downloaded puppy, but I can't seem to find any disks. Is that beacouse I startet it in the memory? I'm runing livecd.

---

### Post by towoha on 2009-07-12
Using fdisk I find it, but I can't access it. Why?

---

### Post by LewRockwell on 2009-07-12
> **towoha said:**
> I have now downloaded puppy, but I can't seem to find any disks. Is that beacouse I startet it in the memory? I'm runing livecd.

downloaded puppy...ok
no disks what?
no disks to burn puppy onto?
what did you start in memory?
which livecd are you running?

I need a nap...

.

---

### Post by towoha on 2009-07-12
> **LewRockwell said:**
> downloaded puppy...ok
no disks what?
no disks to burn puppy onto?
what did you start in memory?
which livecd are you running?

I need a nap...

.

I can't read the disks I have in my computer.
I loaded puppy into memory when I started it from the CD 
The distro is: Puppy Linux 4.2.1 
Burned image to cd, then mounted in computer and runing in memory. Clearer? 
Please, take a nap! Don't let me keep you awake!

---

### Post by jerome1232 on 2009-07-12
> **towoha said:**
> [[IMG]http://thumb15.webshots.net/t/96/96/4/96/17/2638496170102750835KDKeaj_th.jpg[/IMG]](http://good-times.webshots.com/photo/2638496170102750835KDKeaj)

Can't you right click the ext3 partition and assign it a drive letter?

I don't understand the purpose of using Puppy Linux to copy the files to a different area... easier to do in ubuntu (won't have to manually create mount points and mount your partitions)

What did you want to end up doing, get windows to read ext3 or just get the data off that disk and format it to ntfs?

---

### Post by towoha on 2009-07-12
I got it working!!! :-D Finaly I'm able to copy all my files from the old backup disk :-) I had to put the disk in my computer, not use an external usb cabinett. Then i used the EXT2 Volume Manager, asigned a new drive letter to the this (G), restarted the computer, and whops there it is. I read/write with windows explorer =) So now I'm copying everything over to another disk and when I'm finished with that I will reformat the disk to NTFS and backup the most important stuff to G =) Long process, but now it's working.
I have to thank everyone of you that helped me with this! It's been great! 

Regards
Torbjørn 
Norway

---

