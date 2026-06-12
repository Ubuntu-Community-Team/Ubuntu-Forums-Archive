---
title: "Shred malfunction"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Prince Valiant on 2011-05-08
Hi.  

I've just destroyed my HD.  I have an IBM R52, running Windows (/dev/hda1) and Ubuntu.  

I wanted to shred my ubuntu partition (/dev/hda3), so I researched it and found information about the function.  I entered the following into the terminal of Ubuntu 11.04 live boot, from a cd:

```
 sudo shred -v -z -f /dev/hda3 
```

I ran this, and it took about 1 second to complete and return the user prompt for a new command (sorry, I don't know the proper term.)

I opened gparted, which I had used to determine what the proper names of each partition was, and discovered that the whole drive is now considered unallocated free space.

I think, since the shred command took so little time to run, that only the partition table was destroyed.  My guess is that all the files are still intact on the HD. However, I know too little about this to say much for certain.

Is there any way that I can get my WinXP OS back?  I know it's probably asking a lot, but there are things on there I can't lose.  :-(

I really need help.  Anything you can recommend would be greatly appreciated.  Thanks in advance.

-Val

---

### Post by diablo75 on 2011-05-08
This should go without saying... 

Always backup your data, especially if you're about to run the shred command against a hard drive that happens to contain data you don't want to lose.

It sure looks like you had the syntax right but still, running a command like that to do something small or large should always be done with caution.  I had a friend who uses Windows and downloaded some "wiping" utility.  He didn't know what he was doing, thought he was doing something rather tame, and ended up wiping every single JPG on his computer; not just Internet cache but all his own personal photographs (fortunately he had most of this stuff on CDs).

I don't do wiping like this.  If I'm more reason to be paranoid about data being compromised via physical theft I'll use encryption instead.  Wiping files and drives, for me, is something reserved for days when I intend to wipe the whole drive because of the risks involved.

/soapbox

That being said, there are some linux based data recovery terminal-based data recovery programs that might help you.  One is called testdisk and the other is called photorec.  Though your mileage may vary.  For your Window partition I would recommend GetDataBack from Runtime Software (there's a version for FAT32 and another for NTFS... which is probably what your XP install was running).

---

### Post by Prince Valiant on 2011-05-08
Thanks very much, Diablo.

My data is mostly backed up; what I was really worried about was the loss of the Windows OS.    

I'll try testdisk and see if I can get my partitions back.  Will report back with my findings.  

In the meantime, do you have any thoughts on how to use the tool?

-Val

---

### Post by cipherboy_loc on 2011-05-08
Try using testdisk to fix/find your Windows partition.


Cipherboy

---

### Post by Prince Valiant on 2011-05-08
Will do, cypherboy.  Thanks.  :-D

---

### Post by Prince Valiant on 2011-05-08
Something wierd and unexpectedly fortunate to report--in fact, an 'eucatastrophe:'

I removed the HD from the IBM, put it into a case (so that it could function like an external HD), and plugged it into my Acer Aspire One Netbook running Ubuntu 11.04 (originally installed as a beta about 2 weeks before release, and updated since then).

It was immediately recognized, and the "IBM-PRELOAD" partition automatically opened.  I'm copying my files to another external drive as I write.  BTW, the IBM-PRELOAD partition now covers the entire drive -- at least, it claims to be about 60 GB, and that's as big as the drive is.  There used to be a hidden IBM recovery partition, and I don't know what happened to that.  I've not yet dared to open gparted.

Also, I'd tried to boot from the shredded drive before I removed it and copied it; I got as far as the "error: no such partition" problem that Grub has given me before when I've mis-installed it.  

I can hardly guess what has actually happened, or even what was messed up.  Maybe gparted on the live 11.04 disk made some mistakes; maybe the only thing the shred command did was to remove all traces of the /dev/sda3 partition from the MBR.  

Now I've got a new question:  I'm copying all the windows files to my external drive; how can I run windows from them?  Should I use some program (of which I'm still ignorant) to make an image of the disk, or should I install grub to what I've got?  Or should I find a way to install the Windows bootloader? (if I could choose, I'd rather use the windows bootloader and install with wubi.)  

In a nutshell, I'd like to run the same install of Windows I had before.  I'm now pretty sure that's possible.  

Thanks for your help!

-Val.

P.S.  Sorry for the long post.  Just trying to give all information needed.  :-D

---

### Post by bcbc on 2011-05-08
Don't rely just on gparted. Try some other tools like "sfdisk -l" or fdisk. I did something dumb last night and gparted told me my drive was all unallocated. Turns out it was fine - more or less. Windows booted, and I deleted the 'mistake' from Windows.

May not be the same in your case, but it's worthwhile to check .

---

### Post by Prince Valiant on 2011-05-08
I think it is about the same situation, except that I've lost my bootloader.  

Currently, I'm trying to find a way to make an image of the entire drive before making any changes to it, like installing the bootloader.  Anyone know what I could use?  I've looked at dd, but I don't really understand how it's used--not well enough, anyway, to be able to depend on what I can do with it.

Thanks!

-Val

---

### Post by jmszr on 2011-05-08
Prince Valiant,

Clonezilla: [http://clonezilla.org/](http://clonezilla.org/) should be what you want. In the FAQ/Q&A section, Question 21 under System may be of help with booting once you've transferred the image.

---

### Post by Prince Valiant on 2011-05-09
I ran fdisk (under the Aspire One) on the IBM hard drive.  This is the result:

```
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)
```

I guess that partition in particular was singularly destroyed by the shred command.  What does it mean that it "will be corrected by w(rite)"?

Can I run a command 'sudo fdisk /dev/sdc w' and fix the problem?

-Val

---

### Post by Prince Valiant on 2011-05-09
Well, I've fixed the problem for the time being.  I put the broken HD back into the IBM, and (still using the IBM) used a live disk to install ubuntu 11.04 to a flash drive, making sure that Grub was also installed to the flash drive (to avoid writing to the broken HD).  This procedure simply allowed me to easily set up grub so that it could detect my broken hd's partitions.  

Now I can boot the flash drive, and the WinXP OS from the broken & shredded HD shows up--and I can boot into it.  

Next step:  I'll see if I can boot into the IBM recovery partition (hoping it's still there) and restore the HD to factory settings.  Hope that works.  I've seen conflicting reports about whether the MBR will be rebuilt.

Also hoping that Microsoft Office will be included in the recovery partition. :-D

Thanks for all your help!  Jmszr, I would have been very glad for your post, but I realized that I could boot up without backing up.  Thanks a bunch.  

Since the rest of my work is neither Linux based, nor does it seem to be generally useful, I'll count this thread solved.  The first part of this post describes, in a nutshell, what I did that actually worked.

-Val

---

