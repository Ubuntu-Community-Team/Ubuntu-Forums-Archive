---
title: "disc doubler"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by degarb on 2010-02-21
In windows, you have long been able to right click a drive or folder to compress it.  Not to some gz or zip, but seemlessly doubling the capacity.

we used to use disc doubler or stacker.   

Now, I need it or I cannot get my guest vm to work, since I don't have enough space for the install.

---

### Post by falconindy on 2010-02-21
Very few Linux filesystems offer transparent compression like NTFS does. Your choices appear to be Ext2 with e2compr, or Btrfs.

Good luck.

---

### Post by degarb on 2010-02-21
> **falconindy said:**
> Very few Linux filesystems offer transparent compression like NTFS does. Your choices appear to be Ext2 with e2compr, or Btrfs.

Good luck.


I marked for install e2tools  and  btrfs (some experimental file system).  Installing either does nothing.

The source forge page on ecompr is way above anyones head but a programmer with a degree.

---

### Post by 2hot6ft2 on 2010-02-21
Ah, the good old days when ms came out with doublespace. DOS 6.0 I believe it was and in 6.2 they took it out. Word was it was stolen from stacker.

I remember running Norton Speed Disk in windows 3.1 using doublespace and watching windows shrink to a dot in the middle of the screen and vanish.:o

---

### Post by degarb on 2010-02-21
I like the xp folder compression.  So you got a folder to seemlessly compress you check this.  Great for nothing too critical but annoyingly large.  Since confined to folder, only one folder at a time might corrupt.  Now is such was set there is no reason entire folder should be balled to gether.  Each file could be balled individually for less risk. Balling entire drive up to one file is insane, but has its place where no other option is available.

I emailed the source forge to see if english version of e2. It looked like that page gave code that you can put into some source of e2, where ever that is.   Then, even the description of what it does in usage seems like it doesn't do what we want, but probably not true.

---

### Post by degarb on 2010-02-21
Since i really want to compress my vdi file. I would be happy with anything that could transparently compress this file.

---

### Post by degarb on 2010-02-21
Quick reading, it looks like btrfs might be the most promising.  Does gparted have this.  Then, I need to know how to invoke an use it.   

Anyone know?

---

### Post by falconindy on 2010-02-21
[HowTO: Btrfs Root Installation](http://ubuntuforums.org/showthread.php?t=1389279)

Don't expect any miracles. Btrfs is limited to a 4k block size, which means compression isn't fantastic. Make sure you do the initial mount with '-o compress' before copying your data back over.

---

### Post by degarb on 2010-02-21
What kind of compression do you think is possible?  

I got converting down.  Foggy on mounting. 

 Like with many things, alot of steps and crosstalk, when trying to research this, as method seems to evolve quickly.

---

### Post by falconindy on 2010-02-22
Compression is a fickle thing. There's too many variables to pin down an exact number. I gained about 100mb on 150gb of movies, but a 5gb block of zeroes takes up under 1mb with zlib compression.

Not sure what you mean by the method is evolving quickly. It's pretty straightforward and mimics the same process you'd go through to alter your root regardless of the new FS being put in place. I didn't go the convert route, I wanted a clean start. It's as "simple" as:
0) Install btrfs-progs and double check other pre-requisites (zlib, kernel config)
1) Back up your stuff
2) Reformat the drive
3) Copy everything back
4) Update /etc/fstab
5) Update bootloader
6) Update boot image
7) Reboot

It's plastered all over the place, but I suppose it's worth mentioning yet again: BTRFS is experimental. It may kick your cat. That said, I've been loving it for the past 3 months.

---

### Post by degarb on 2010-02-22
I don't know what line to put in the fstab.   something about uuid.  I don't know

I just tried to mount with    sudo mount -o compress /dev/sda1  but it complained not found in ftab.    I don't see any info on what to add to it or how to determine the long id that the drive has.

---

### Post by degarb on 2010-02-22
I tried adding UUID=b097377e-45e8-472b-ba7d-aa226511a679/             btrfs   defaults,compress 0      1 

to fstab.  never edited one before.  I don't know how to deal with wrap, or sure is correct or what is needed.   I got the id from root nautist name of drive, since no reference was there to anything else.  I also couldn't type any mount commands, as the disc was constantly auto mounting.  I don't know if to do with any program open. 

I think the implementation needs to be rethought to make this something enjoyable and comprehendable and doable.   but, anyway.  

i didnt get any compression yet.

---

### Post by falconindy on 2010-02-22
The guide I posted goes over this.

> **ibuclaw said:**
> [COLOR="Sienna"][SIZE="3"]Update Fstab[/SIZE][/COLOR]
The conversion process creates a new UUID for the partition, as such this requires updating.

To obtain the new UUID, run:
```
blkid /dev/sda5
```
Make a note, then edit /etc/fstab
```
nano /etc/fstab
```
I've highlighted the areas of interest that require changing - don't forget to update the file system type too.
**Before**:
```

# / was on /dev/sda5 during installation
UUID=e03cb3cc-8470-4ee6-a18a-b49da45c6f21 /             ext4    error=remount-ro 0      1

```
**After**:
```

# / was on /dev/sda5 during installation
UUID=[COLOR="Red"]4be84d08-94cb-4013-ae0b-ce1d72d96db1[/COLOR] /             [COLOR="Red"]btrfs   defaults        [/COLOR] 0      1

```

---

### Post by degarb on 2010-02-22
> **falconindy said:**
> The guide I posted goes over this.

I hit mount I can see my external usb drive  on sdb1

Thanks.  Unfortunately, when I do blkid -o value -s UUID /dev/sdb1

or even 

blkid -o value -s UUID /dev/sdb1


Nothing is printed out, nor is there any naturally occiring reference to sdb anywhere.  there is a natural reference to the internal drive  sda1 and the swap sda5.

---

### Post by degarb on 2010-02-22
I think blkid doesn't work for external usb drives, and so the you cannot properly edit the fstab to get compression.  Am I missing something.  Need others to confirm.

---

### Post by falconindy on 2010-02-22
blkid works for anything. Period. It's an integral part of the boot process and therefore needs to be a very flexible piece of software. If you're getting no output back from blkid, then the drive isn't mounted, or you're specifying it incorrectly.

Example of blkid on my USB drive:
```
$ blkid /dev/sde1
/dev/sde1: LABEL="Flashy" UUID="6E1B5F1E742ED9F4" TYPE="ntfs"
```

Regardless, you can mount a drive by label (e.g. LABEL=Flashy) or device name (e.g. /dev/sde1) rather than UUID (e.g. UUID=6E1B5F1E742ED9F4).

---

### Post by degarb on 2010-02-22
Only after unmounting,  I got a return of,
UUID="b097377e-45e8-472b-ba7d-aa226511a679" UUID_SUB="c32a98e4-0cd6-4fc2-85c6-d35e6661fc2f" TYPE="btrfs" 

then, in fstab I didn't see anything related to this drive  so I added.
UUID=b097377e-45e8-472b-ba7d-aa226511a679 /             btrfs   defaults,compress 0      1

I then manually sudo mount /dev/sdb1    and mount says it is mounted in /

I did a search but don't see it attached to file system.  I am doing something wrong.

---

### Post by Ocxic on 2010-02-22
If you do that your performance will most likely be really crappy.

---

### Post by degarb on 2010-02-22
Will see if crappy.  And report back.  The drive gets tossed if no seemless compression and I go out and buy a new harddrive--untested, made in china, and even higher probability of early failure.  Then someday, I might throw the new drive out for space constriction reason. 

  I might have solved and figured out my mistake: 
I figured out I needed to change the / to /mnt/xhd  then gksu nautilus  to create this folder , then change the permissions to allow writing and reading.   then reboot for settings to take effect.   I couldn't get it to unmount any method tried.

Now the btrfs drive mounted.   It still says 1.5 gig,  I will see now if enough room to install windows 2000 that needs 2 gig free for an install, even as a guest os on virtual box. 


I don't know if this will work, since I am guessing the reported disc free space wont change.   Maybe even file size reporting might not change.    


So to recap,  I snapticed btfs,  did a mkfs -t btfs  /dev/stb1   which wiped the drive and put new file system.  then unmounted the drive and blkid /dev/stb1   then sudo gedit /etc/fstab  then did the steps in paragraph one of this post.     

AmI missing any steps?

---

### Post by falconindy on 2010-02-22
> **Ocxic said:**
> If you do that your performance will most likely be really crappy.
If you're referring to transparently compressing the drive, I'm sorry but you're going to be wrong 9 times out of 10. Hard drive I/O is the slowest operation a computer performs. By compressing the data on the disk, you reduce the amount of data that the hard drive needs to read. The tradeoff, of course, is that the CPU spends a few extra cycles decompressing this data on the fly. On a modern system (built in this decade), those few extra clock cycles required are not an issue.

[QUOTE=degarb]I then manually sudo mount /dev/sdb1 and mount says it is mounted in /

I did a search but don't see it attached to file system. I am doing something wrong.[/quote]Help me out here with a little context. It sounds to me like you're mounting your external drive directly on top of the root filesystem? That's just a bad idea. If you manage to successfully do this, you **will** crash, and you **will** need to fix it from a live CD.

---

### Post by degarb on 2010-02-22
> **falconindy said:**
> If you're referring to transparently compressing the drive, I'm sorry but you're going to be wrong 9 times out of 10. Hard drive I/O is the slowest operation a computer performs. By compressing the data on the disk, you reduce the amount of data that the hard drive needs to read. The tradeoff, of course, is that the CPU spends a few extra cycles decompressing this data on the fly. On a modern system (built in this decade), those few extra clock cycles required are not an issue.

Help me out here with a little context. It sounds to me like you're mounting your external drive directly on top of the root filesystem? That's just a bad idea. If you manage to successfully do this, you **will** crash, and you **will** need to fix it from a live CD.
then, in fstab I didn't see anything related to this drive  so I added.
UUID=b097377e-45e8-472b-ba7d-aa226511a679 /             btrfs   defaults,compress 0      1

I think you are saying that the above line will mount the ext hard drive over file system.   It didn't happen just didn't see anything related to stuff on drive.   I then changed the line to 
UUID=b097377e-45e8-472b-ba7d-aa226511a679 /mnt/xhd             btrfs   defaults,compress 0      1

which still didn't do anything.  So I super usered to create this folder.  Still nothing.  I rebooted and now see the harddrive contents there.

I am unsure if I will get any compression.  So far, I am installing 2000 as guest in vbox with vdi here.  If the install works, then I am getting compression.  If near end I get disk full message, then not.   The installer unpacks a huge amount of temp files, which aren't deleted until end of install.  I notice xp and 2000 no longer offered user options not to install ie, notepad, calculator etc, to save space.  Instead they forced people to buy new hardware to support the blooming OS.  The vendors of the hardware loved this, as they can now milk you prematurely of your dollars.

---

### Post by falconindy on 2010-02-22
> **degarb said:**
> then, in fstab I didn't see anything related to this drive  so I added.
UUID=b097377e-45e8-472b-ba7d-aa226511a679 /             btrfs   defaults,compress 0      1

I think you are saying that the above line will mount the ext hard drive over file system.   It didn't happen just didn't see anything related to stuff on drive.   I then changed the line to 
UUID=b097377e-45e8-472b-ba7d-aa226511a679 /mnt/xhd             btrfs   defaults,compress 0      1

which still didn't do anything.  So I super usered to create this folder.  Still nothing.  I rebooted and now see the harddrive contents there.

I am unsure if I will get any compression.  So far, I am installing 2000 as guest in vbox with vdi here.  If the install works, then I am getting compression.  If near end I get disk full message, then not.   The installer unpacks a huge amount of temp files, which aren't deleted until end of install.  I notice xp and 2000 no longer offered user options not to install ie, notepad, calculator etc, to save space.  Instead they forced people to buy new hardware to support the blooming OS.  The vendors of the hardware loved this, as they can now milk you prematurely of your dollars.

And I thought I was insane...

If you mount with the 'compress' option, you're getting compression. Period. Like I mentioned earlier, there's no telling how much compression you'll get away with since it varies so much depending on what it is you're compressing.

---

