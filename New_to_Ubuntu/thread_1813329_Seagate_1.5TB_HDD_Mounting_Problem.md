---
title: "Seagate 1.5TB HDD Mounting Problem"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by Da Physicist on 2011-07-27
Hello everyone,

I'm sad to say that my first post on these very useful forums is gunna have to be one on a problem I am having my very reliable external HDD. Today I loaded up my W7 partition (which I hardly ever use) to update my iPod's OS via iTunes. I then noticed that one of my directories in my Music file was corrupted. I decided to finally try the disk checker to look for what was casing this corrupted director (as I'd rather not have to redownload around 10 GB of music).

After letting it run for a few hours, it eventually froze. I hit cancel, which it did happily, refusing to mount the plugged in HDD like it usually does. I removed the unmounted drive and plugged it back in only to find that Windows would not mount it due to a corrupted file system.

I then did what anyone would do when confronted with this problem. I loaded up Ubuntu 11 and ran Disk Manager to check if the file system really was corrupted, which it was not. However, mounting to Ubuntu failed and returned the following error:

```
Error mounting: mount exited with exit code 18: 
Failed to open $MFT/$BITMAP: No such file or directory
Failed to load $MFT: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory
```

I know this is pretty much a death sentence for the drive, but what I noticed was the $MFT MIRROR wasn't missing, so this gave me a bit of hope. I ran ntfsfix and it returned:

```
joey@MobileCOM-Ubuntu:~$ sudo ntfsfix /dev/sdb1
Mounting volume... Failed to open $MFT/$BITMAP: No such file or directory.
ntfs_mft_load(): Failed.
Failed to load $MFT: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Failed to open $MFT/$BITMAP: No such file or directory.
ntfs_mft_load(): Failed.
Failed to load $MFT: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.
```

Running chkdsk on several W7 machines doesn't even get past a microsecond, as an error automatically pops up saying it is impossible to do so.

So, there is about 250 GB of the past three years of my life on this backup drive (which is almost always spun down when not in use). A lot of my research projects data is stored on this drive as well. Therefore, I am completely open to any suggestions by you guys. My last resort will be to do a low-leveled data extraction and then reformat it.

Anyway, suggestions?

Warm Regards,
Joe Glaser

---

### Post by oldfred on 2011-07-27
Welcome to the forums.

You can try this:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

And if that does not work:
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I have used photorec and it worked but was tedious, took a long time to scan drive, does not recover file names as they are gone. But some files have the names embedded which can then be recovered.

---

### Post by Da Physicist on 2011-07-27
Hey oldfred,

Thanks for your quick reply. I installed testdrive (which I was surprised to see I didn't have installed already), selected the drive and hit [Boot]. The following appeared:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 1500 GB / 1397 GiB - CHS 182401 255 63
     Partition                  Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1 182400 254 63 2930272002 [FreeAgent Drive
]
Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

It seems both sectors are fine (which is odd knowing at least the main MFT is corrupted). So I ran the [LIST] option, which said that it couldn't as the file system is corrupted. I went back and selected the [REBUILD MFT] option and it returned:

```
MFT and MFT mirror are bad. Failed to repair them.

```

Which is likely my death sentence. Now, you suggested I try to rebuild my boot sector. I would just like to make sure that by doing this, it will not harm my ability to access my data later.

If this fails, then it seems that I will need to create an image of the filesystem and try to extract my data through that. Now the options in the Ubuntu Data Recovery page suggest methods that seem extremely tedious considering I'll have to recover around 300 GB of files one file at a time. Is this correct and if so, is there a faster way of doing this?

Warm Regards,
Joe Glaser

---

### Post by Mark Phelps on 2011-07-27
I've had consistently good results recovering damaged NTFS filesystems using Runtime Software's GetDataBack for NTFS.

You can download the trial version from their site -- but you need to install it on a Windows PC.  And, the trial version will only do the recovery scan, it will not actually recover the files.

But, it DOES preserve the filenames and directory structures.  So, you can at least see what it can find.

I would let it run overnight to do an in-depth scan.

---

### Post by Da Physicist on 2011-07-27
Hello Mark,

Thanks for this information. Does the program effect the chances of data recovery later, should I choose a different program? I'll try running the try later tonight if it doesn't. 

I did access something in TestDisk which gave me a list of files from my system (not directly through the [LIST] option though), so at least they are still there. Now, the question is: should I bother trying to rebuild the boot sector and if so, will this hurt my chances of data recovery? If it fails, exactly what steps should be taken for the best results from the data recovery. I am likely off to buy a backup HDD to store the data into. Thanks again the the support so far and keep the ideas rolling!

Warm Regards,
Joe Glaser

---

### Post by Da Physicist on 2011-07-27
Hey All,

Here's an update. So the TestDisk option fell through the floor. The MFT  recovery failed, as did the [Rebuild Boot] option. The file system is  just too far gone to be salvaged, which makes me and everyone around me  wonder what the hell Windows did to this poor HDD.

I am currently running GetDataBack for NTFS on the HDD. It's scanning  through all the sectors and has already found 429 file starts, so the  stuff is still there. I'm gunna let it run over night. Tomorrow, I  should have a list of all the files that are still in my HDD that can be  salvaged. It's gunna take around 5 hours to go through all the sectors.  

Once the files are found, I am switching over to Ubuntu to run the  GDDrescue on the HDD and see what it returns after a few runs. The files  will be saved to a new Western Digital 2 TB External HDD I just picked  up at Target (thank you old gift cards xD).

I will update this thread as I make progress. I hope to at least turn  this experience into a Data Restoration topic so that future Google  Searchers will be able to get at least some of their data back from the  dead.

Again, thank you two for your help so far. To the rest of you, any ideas  are welcome if you know a quicker way to do a repair/restoration.

Warm Regards,
Joe Glaser

---

### Post by Mark Phelps on 2011-07-28
> **Da Physicist said:**
> I am currently running GetDataBack for NTFS on the HDD. It's scanning  through all the sectors and has already found 429 file starts, so the  stuff is still there. 

That's GREAT news!

If you want to use GetDataBack to do the actual file recovery, you can simply purchase it online, download the serial key, install it -- and then recovery your files. This saves you the trouble of reinstalling the product and running the scan all over again.

---

### Post by Da Physicist on 2011-07-28
Hey Mark,

The scan ran overnight and returned all the files that where on the HDD originally. I saved the scan to my Windows Partition. I currently just spent the same amount of cash for another HDD so I think I'm gunna try out GDDrescue first, run a few passes, and see what it returns. If it only returns some of the files, I'll try out GetDataBack for NTFS's purchase. It's too bad it costs so much to get a program like it.

I have the set up at the coolest room in my house currently and I'm watching it via TeamViewer from my work. Time to do some final reading and start up the retrieval.

Warm Regards,
Joe Glaser

---

### Post by Da Physicist on 2011-07-28
Mid-Day Update:

At approx. 11:45pm EST I began running GDDrescue's HDD Imaging Process. It has moved through approx. 250,000 MB of data at a speed of 15240 KB/s. This means the process should take around 20.534966 hours to crunch through the approx. 1.3 TB of useable space on the HDD. I do like the fact I can start and stop GDDrescue at any moment and pick it up where I left off via the logfile, meaning I can let the HDDs rest a bit if the room starts to heat up.

After this finishes, I'll be grabbing as much data as I can get off the HDD. I'll update it as it goes, but I do have one request. Anyone know of a good success rated low-level recovery program for either Ubuntu or Windows 7 that can read this image? Cause if Foremost doesn't work, I'll need some other options.

Warm Regards,
Joe Glaser

---

### Post by oldfred on 2011-07-28
Photorec did work for me, but it cannot recover file names, just extensions or types. You can easily rename photos & music as they have internal names. But I had many text files and had saved some many times. Linux writes to a different place on every rewrite, so it found every old copy of my text files & I was never sure I found the last one. And I had to grep data from inside the files to know which was the one I was trying to review.

---

### Post by Da Physicist on 2011-07-29
Morning Update:

Thanks for the info oldfred. The imaging finished today around 10am EST. I've been told by a few friends of mine to try out GetDataBack's recovery process. So I got hold of a friends copy and I must say, it's 20% done and all my data is coming out perfectly, file directories/names as well. I'll let you guys know later how this turns out.

Warm Regards,
Joe Glaser

---

### Post by cmcanulty on 2011-07-29
Try this it won't hurt
```
sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall
```

---

