---
title: "Think I may have just lost everything."
date: 2009-04-19
forum: New to Ubuntu
---

### Post by TMcMahon51 on 2009-04-19
I was resizing my partition earlier to give more space for Ubuntu, when the power went out. I switched the PC back on, to get an Error 17 in Grub. I went to the Live CD, and it seems the Ubuntu Partition is seriously screwed.



[http://i42.tinypic.com/2yor2h5.png](http://i42.tinypic.com/2yor2h5.png)


Please, tell me that this is fixable. I just transferred my comic collection over from the Windows partition the other day, and stupidly, did not create a backup. I'd literally rather have my legs cut off, than to lose my whole collection. D:

---

### Post by DGortze380 on 2009-04-19
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by .:PiXi²:. on 2009-04-19
Try [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").
It recovers a whole lot more than only pictures, see [here.]("http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec")

---

### Post by starcannon on 2009-04-19
+1 to PhotoRec, its a pain in the asterik, but comes in handy when these sorts of things happen.

GL

---

### Post by ashmew2 on 2009-04-19
> **TMcMahon51 said:**
> I was resizing my partition earlier to give more space for Ubuntu, when the power went out. I switched the PC back on, to get an Error 17 in Grub. I went to the Live CD, and it seems the Ubuntu Partition is seriously screwed.



[http://i42.tinypic.com/2yor2h5.png](http://i42.tinypic.com/2yor2h5.png)


Please, tell me that this is fixable. I just transferred my comic collection over from the Windows partition the other day, and stupidly, did not create a backup. I'd literally rather have my legs cut off, than to lose my whole collection. D:

I'm sorry man =( .  I hope you get your stuff back!

---

### Post by TMcMahon51 on 2009-04-19
Currently using Photorec right now, but it's making hundreds of files that are locked, and won't open.


I've re-installed Ubuntu 8.04 and completely updated onto /dev/hda4 (original install is on /dev/hda2). Is there something I screwed up?



PS: Would it be possible for Photorec to completely recover my WoW folder intact?

---

### Post by starcannon on 2009-04-19
After the files are recovered you may need to change the ownership of them(get rid of the locks), thats not to tough.

Not sure if recovering the WoW folder is a great idea; if you have some screenshots you want to keep, just grab those out. I don't think Photorec recovers file names, just the files themselves.

---

### Post by TMcMahon51 on 2009-04-19
Only reason I want to recover wow Folder is my custom UI, which took me upwards of 15 hours to create, as well as 2 of the addons I developed.


The other reason is, as you mentioned, a few screenshots.


BTW, is there any way to rebuild the filesystem without losing data? With fdisk -ls, /dev/hda2 still shows up, but seems unmountable.

---

### Post by bumanie on 2009-04-19
When one is part way through partitioning and has a power outage, I don't believe the filesystem can be rebuilt. But as the others have said, photorec should be able to recover most, if not all you data.

---

### Post by TMcMahon51 on 2009-04-19
Thanks for the help so far.


Is there any way to change ownership of all the folders at once? There's over 700 of them, and, changing them all one at a time would likely take me a few days. =\


EDIT: Nevermind, already figured it out.

After changing the ownership, and checking them, it seems it was just about half a million .txt files, and not any of my actual data. >.<


Somebody else I know recommended that I try to use testdisk, but didn't say how, or what to do with it. Good idea, bad idea, or worthless to even attempt?

---

### Post by DGortze380 on 2009-04-19
> **TMcMahon51 said:**
> 
I've re-installed Ubuntu 8.04 and completely updated onto /dev/hda4 (original install is on /dev/hda2). Is there something I screwed up?


Unfortunately, this may have been your problem. 

Rule #1 in data recovery ... DO NOT MOUNT THE DRIVE
Rule #2 ... Image the drive and work from the Image

It is likely that, depending on your previous partitioning scheme, you've overwrite any data that may have been recovered from that section of the drive.

Do try other recovery tools, you may get more.
Helix is a more professional option if you want to spend the time.
TestDisk is another option: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Last suggestion is verify that all those text files are actually text files, a hexeditor would make quick work of some of them. It is possible (possible.. likelihood unknown) that PhotoRec recovered a 'text file' that was actually another format.

---

### Post by TMcMahon51 on 2009-04-19
Disk /dev/hda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 28778 254 63  462334572
No EXT2, JFS, Reiser, cramfs or XFS marker
 2 P Linux                28779   0  1 34989 254 63   99779715
 2 P Linux                28779   0  1 34989 254 63   99779715
 3 P Linux Swap           38693   0  1 38912 254 63    3534300
 4 P Linux                34990   0  1 38692 254 63   59488695




Number 2 would be where the botched install is. Seeing as it's coming up in testdisk, would that mean it's salvagable?


If not, I would like to know, as it would be a waste to go load my shotgun and not use it. =\

---

### Post by DGortze380 on 2009-04-19
> **TMcMahon51 said:**
> Disk /dev/hda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1 28778 254 63  462334572
No EXT2, JFS, Reiser, cramfs or XFS marker
 2 P Linux                28779   0  1 34989 254 63   99779715
 2 P Linux                28779   0  1 34989 254 63   99779715
 3 P Linux Swap           38693   0  1 38912 254 63    3534300
 4 P Linux                34990   0  1 38692 254 63   59488695




Number 2 would be where the botched install is. Seeing as it's coming up in testdisk, would that mean it's salvagable?


If not, I would like to know, as it would be a waste to go load my shotgun and not use it. =\

It really depends a lot on how it was previously partitioned ... before the power issue.

---

### Post by Ticketoride on 2009-04-19
> **TMcMahon51 said:**
> After changing the ownership, and checking them, it seems it was just about half a million .txt files, and not any of my actual data
That's File Corruption. Happened to me under Windows too, trying to recover my Files, and the best the Recovery Program could do is pick up whatever Thousands of itty-bitty File Fragments which were left. Hopefully you find a Way.

---

### Post by TMcMahon51 on 2009-04-19
|Windows| |Free space| |hda2| |swap| |hda4|

The free space was being assigned to hda2, if that helps.

---

### Post by DGortze380 on 2009-04-19
> **TMcMahon51 said:**
> |Windows| |Free space| |hda2| |swap| |hda4|

The free space was being assigned to hda2, if that helps.

It's really hard to give you a definite answer... here's a bit of theory...


If your original install was on "hda2", and "hda4" was unallocated space or a separate partition... AND, "hda2" has not moved, and "hda4" has not moved, and nothing new has been written to "hda2", if may be possible to recover your data...

that's a horribly condensed explanation, but you can see why I can't give a definitive answer.

try making an image of the drive and using Helix.

To image the drive, boot a live CD, Do not mount your hard drive, attach a secondary drive of some sort, internal, external, you choose. You'd use a command similar to:

sudo dd if=/dev/hda of=/media/myExternal/image.dd

---

### Post by TMcMahon51 on 2009-04-19
****.


Well, time to go blow my ******* brains out, as the majority of that data was ******* irreplacable.

---

### Post by DGortze380 on 2009-04-19
> **TMcMahon51 said:**
> ****.


Well, time to go blow my ******* brains out, as the majority of that data was ******* irreplacable.

You may want to look into the rsync command for future use.

---

### Post by mikechant on 2009-04-20
It's not clear - did you actually try testdisk in the end? If so, what happened?

If looks as if you might have had a chance of recovery if
a) The freespace area was at least as big as the following partition that you were expanding
or
b) the partitioning operations had not got to the point of overwriting where the old start of hda2 was when the power went out.

In either of these cases you should have had a chance of recovering the old sda2 intact.

---

### Post by john stiles on 2009-04-20
Sorry for your comic collection loss. Don't forget about fire and theft in your future backups. I send a six monthly DVD to Mum.

---

