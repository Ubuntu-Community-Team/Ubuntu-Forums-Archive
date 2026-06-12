---
title: "GRUB Error 18"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by knidsrok on 2009-04-05
I've had 8.10 running on an old Dell E310 desktop for maybe six months now without any major problems.  Last night it froze up pretty bad, and now today, when I tried to start it up again, it gives me "Error 18" after trying to load GRUB.

I've searched around the forum about this kind of problem, which seems to occur primarily with new installations -- the recommended solutions invariably involve reinstalling Ubuntu and overwriting the hard drive.

Is there anything I could try first that wouldn't involve my having to start over from scratch?

---

### Post by unutbu on 2009-04-05
I think your problem should be fixable without having to reinstall.
Please follow the instructions here [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) to run boot_info_script.
Post the RESULTS.txt file here.

---

### Post by knidsrok on 2009-04-05
Ok, I've got the results of the boot info script, and am pasting them below tagged as code.  Thank you so much (in advance) for taking a look at this for me!

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009b4a6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   973,812,104   973,812,042  83 Linux
/dev/sda2         973,812,105   976,768,064     2,955,960   5 Extended
/dev/sda5         973,812,168   976,768,064     2,955,897  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="334ccdc6-f0e6-48ed-a856-9064560a8aa4" TYPE="ext3" 
/dev/sda5: UUID="a3022505-1b5c-4528-bc24-44a110eb4310" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

---

### Post by knidsrok on 2009-04-05
Just posting to bump the thread back up, as I noticed it slipped off the first page of the forum.

I'm really hoping someone can help me out with this.

---

### Post by rhcm123 on 2009-04-05
> **knidsrok said:**
> Ok, I've got the results of the boot info script, and am pasting them below tagged as code.  Thank you so much (in advance) for taking a look at this for me!

```

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



```
According to this, your filesystem was corrupted during the crash. Do you have a copy of the live CD? You can use the fsck command to check the partition and repair the damage.

> **knidsrok said:**
> Just posting to bump the thread back up, as I noticed it slipped off the first page of the forum.

I'm really hoping someone can help me out with this.
Please note it is also forum policy only to bump threads if they have been abandoned for over 24 hours. :)

---

### Post by unutbu on 2009-04-05
Yes, knidsrok, I agree with rhcm123. It looks like the abrupt shutdown has left your filesystem in a corrupted state. 

To fix this, boot from the LiveCD, open a terminal, and type
```

sudo fsck -CM /dev/sda1
```

fsck will try to repair your filesystem. Doing so may result in some data loss -- e.g. loss of files that had not been written to disk at the time of the abrupt shutdown. 
Depending on how many "inodes" need repair, you may be asked a lot of questions. I know of no other way to handle this situation except to say yes. 

If you get tired of saying yes, you may type Ctrl-C to break out of fsck, and then type ```


sudo fsck -yCM /dev/sda1
```

This will run fsck, and automatically answer yes to all questions.

Let me be clear: After fsck is done running, you may find there is some data loss. Probably, there won't be much data loss, but I can't guarantee it. And actually, what data loss you find is data loss that has already occurred, whether you run fsck or not. 

PS. To avoid this problem in the future, if the machine ever apperas frozen, try shutting down by typing 
```

Alt-SysRq-R  # turns off keyboard raw mode and sets it to XLATE
Alt-SysRq-E  # send a SIGTERM to all processes, except for init.
Alt-SysRq-I  # send a SIGKILL to all processes, except for init.
Alt-SysRq-S  # attempt to sync all mounted filesystems.
Alt-SysRq-U  # attempt to remount all mounted filesystems read-only.
Alt-SysRq-O  # poweroff
```

Type each key combination (REISUO) in order. Pause a few seconds in between each key combination. This will shutdown your machine more gently.

Good luck. Let us know how it goes.

---

### Post by knidsrok on 2009-04-05
Thanks for the help, and sorry about the etiquette-violating bump.  Won't happen again.

Right, so, I booted up with the live CD, figured out how to use the fsck command, and ran it on /dev/sda1, and got an error message saying:

> fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

(It is most emphatically NOT a zero-length partition, as it contains about 495 of my hard drive's 500 GB.)  

I ran a google search on the error message text, but I'm unable to gather what I should do next from any of the results.

Any ideas?

---

### Post by knidsrok on 2009-04-05
> **unutbu said:**
> Yes, knidsrok, I agree with rhcm123. It looks like the abrupt shutdown has left your filesystem in a corrupted state. 

To fix this, boot from the LiveCD, open a terminal, and type
```

sudo fsck -CM /dev/sda1
```

fsck will try to repair your filesystem. Doing so may result in some data loss -- e.g. loss of files that had not been written to disk at the time of the abrupt shutdown. 
Depending on how many "inodes" need repair, you may be asked a lot of questions. I know of no other way to handle this situation except to say yes. 

If you get tired of saying yes, you may type Ctrl-C to break out of fsck, and then type ```


sudo fsck -yCM /dev/sda1
```

This will run fsck, and automatically answer yes to all questions.

Let me be clear: After fsck is done running, you may find there is some data loss. Probably, there won't be much data loss, but I can't guarantee it. And actually, what data loss you find is data loss that has already occurred, whether you run fsck or not. 

PS. To avoid this problem in the future, if the machine ever apperas frozen, try shutting down by typing 
```

Alt-SysRq-R  # turns off keyboard raw mode and sets it to XLATE
Alt-SysRq-E  # send a SIGTERM to all processes, except for init.
Alt-SysRq-I  # send a SIGKILL to all processes, except for init.
Alt-SysRq-S  # attempt to sync all mounted filesystems.
Alt-SysRq-U  # attempt to remount all mounted filesystems read-only.
Alt-SysRq-O  # poweroff
```

Type each key combination (REISUO) in order. Pause a few seconds in between each key combination. This will shutdown your machine more gently.

Good luck. Let us know how it goes.

Thanks for all the tips, particularly the kinder, gentler shutdown instructions -- hopefully they'll prevent any repeat performances in the future.

---

### Post by rhcm123 on 2009-04-05
> **knidsrok said:**
> Thanks for the help, and sorry about the etiquette-violating bump.  Won't happen again.

Right, so, I booted up with the live CD, figured out how to use the fsck command, and ran it on /dev/sda1, and got an error message saying:



(It is most emphatically NOT a zero-length partition, as it contains about 495 of my hard drive's 500 GB.)  

I ran a google search on the error message text, but I'm unable to gather what I should do next from any of the results.

Any ideas?

exactly what command did you run?

---

### Post by knidsrok on 2009-04-05
> **rhcm123 said:**
> exactly what command did you run?

Well, first I did just plain "sudo fsck /dev/sda1"

Then, after reading Unutbu's reply, I ran it with the "-cm" part.

The results were the same.

---

### Post by unutbu on 2009-04-05
Boot from the LiveCD. 
Open a terminal.
Type
```

sudo dumpe2fs /dev/sda1 |  grep superblock | awk {'print $4'}

```
This command will print a list of numbers, like this:
```
dumpe2fs 1.41.3 (12-Oct-2008)
0,
32768,
98304,
163840,
229376,
294912,
819200,
884736,
1605632,
2654208,
4096000,
```
These are the location of the superblocks. The superblocks hold all the information about your ext3 directory structure. (It plays the same role that the file allocation table (FAT) does on a Windows FAT filesystem). The superblock at 0 is the main superblock, the others are all backups. 

Since the regular fsck command complained that sda1 looked like a zero-length partition, I am guessing that perhaps the superblock at 0 is wrong, and we should ask fsck to read the next superblock.

Here is the command to run fsck, using the superblock at 32768.```

sudo fsck -b 32768 -f /dev/sda1
```

---

### Post by knidsrok on 2009-04-05
> **unutbu said:**
> Boot from the LiveCD. 
Open a terminal.
Type
```

sudo dumpe2fs /dev/sda1 |  grep superblock | awk {'print $4'}

```
This command will print a list of numbers, like this:
```
dumpe2fs 1.41.3 (12-Oct-2008)
0,
32768,
98304,
163840,
229376,
294912,
819200,
884736,
1605632,
2654208,
4096000,
```
These are the location of the superblocks. The superblocks hold all the information about your ext3 directory structure. (It plays the same role that the file allocation table (FAT) does on a Windows FAT filesystem). The superblock at 0 is the main superblock, the others are all backups. 

Since the regular fsck command complained that sda1 looked like a zero-length partition, I am guessing that perhaps the superblock at 0 is wrong, and we should ask fsck to read the next superblock.

Here is the command to run fsck, using the superblock at 32768.```

sudo fsck -b 32768 -f /dev/sda1
```

When I run the dumpe2fs(...) command you suggested, it worked for a while, and then gave me pretty close to same error message as fsck did:

```
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
filesystem
```

That can't be good, can it?

But, seriously, dude -- thanks for all the detail and explanation in your responses.  I really appreciate it.



Seriously, dude, thank you for all the details and explaining in your responses.

---

### Post by unutbu on 2009-04-05
I'm not sure that the following will work, but it is safe and perhaps it will help.
Using google I've found a case similar to yours ([http://www.linuxquestions.org/questions/linux-hardware-18/fsck-could-this-be-a-zero-length-partition-508099/](http://www.linuxquestions.org/questions/linux-hardware-18/fsck-could-this-be-a-zero-length-partition-508099/)). The guy's solution seems to suggest the problem may be in the partition table rather than in the filesystem. 

If that is the case, perhaps try this:

Boot from the Live CD.
Open a terminal.
Type
```

sudo apt-get testdisk
sudo testdisk

```

This downloads and runs the testdisk program. 

Select "No Log", "Proceed", "Intel", "Analyse", "Quick Search".
When asked "Should  TestDisk search for partition created under Vista", answer Y if you have a Vista partition, N otherwise. (It looks like you don't have a Vista partition...)


Press enter, then select "Deeper Search". This may take a while.
Please post the result of the deeper search that testdisk displays.

Use the up/down arrows to move among your partitions.
[B]Press 'p' to try to list files inside the partitions
In particular, check if you can see your files in sda1.[/B]

---

### Post by knidsrok on 2009-04-05
Ok, so I was able to get a list of alternative superblock locations with ```
sudo mke2fs -n /dev/sda1
``` and then tried running fsck on a bunch of them using the syntax you recommended...

...and now I'm getting this error message:```
fsck.ext3: Device or rsource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```

Following the cues from an old support forum thread I found via google, I then used "init 1" to make sure I was in single use mode,  and ran the fsck command from the root prompt.  Same error.

---

### Post by unutbu on 2009-04-05
When you say you are getting the same error, do you mean
```

fsck.ext3: Device or rsource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```
or 
```

fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1 
Could this be a zero-length partition?

```

If it is saying the filesystem is mounted, that is actually an encouraging sign. 
Can you see the files in the filesystem?

You can type

```
mount
```

to learn where /dev/sda1 is mounted.

If, on the other hand, it is saying the partition has zero-length, then try using testdisk.

---

### Post by unutbu on 2009-04-05
I have to go now. I'll be back tomorrow.
Please let us know how it goes.

---

### Post by rhcm123 on 2009-04-05
EDIT: Durr... why did i quote the wrong post :)
> **knidsrok said:**
> 
...and now I'm getting this error message:```
fsck.ext3: Device or rsource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?
```


is the filesystem mounted? This error could also come from leaving gparted running in the background.
Speaking of parted, could you print your partition table for me? Run the following command:
```
sudo parted /dev/sda 
```
Then, on the prompt that pops up, type "print" (no quotes). Copy the results, then type "quit" to exit.

---

### Post by knidsrok on 2009-04-06
Ok, so, since I last posted last night, I've managed to make things much, much worse.

So, I ran the Testdisk program you told me about, though "sudo apt-get" didn't work, so I had to download it and install/run it manually.  Once Testdisk was up and running, I followed the procedure you suggested, and though it returned information about the size and block locations of my two partitions, it couldn't look inside sda1 and see any of its files -- the error message said that it seemed there was something wrong with my filesystem.

Here's where I'm pretty sure I screwed the pooch: having reached the end of what you'd talked about, I ended up following the testdisk datarecovery instructions, and allowed it to write the partition table it had gotten from its deeper search.  Wish I hadn't done that.

When I booted back up, BIOS told me I had "no boot device available."  Somehow, it not only didn't recognize my HD, it had also decided not to recognize my CD/DVD drive either.  By going into the BIOS settings and changing the boot preference so that the CD/DVD drive was the first and only active device, I managed to get it to try booting from the disk.

First I'd see some error messages go by.  Then the Live CD menu would come up, but when I told it to run from the CD, I got yet more error messages, and after a while, it stopped and left me with a prompt called "initramfs."

I told it to reboot, and since then, I haven't been able to get to boot from CD/DVD at all.  So I instead put the Live CD into my Macbook, ran Ubuntu off the disk, and used it to create a bootable flash drive.  At the very least, my desktop will still happily try booting off that.  First however, it tells me:

```
Drive 1 not found: Serial ATA, SATA-2
Drive 3 not found: Parallel ATA, PATA-1 (PRI Slave)
Strike the F1 key to continue, F2 to run the setup utility
```

Then I get the Ubuntu Live CD menu, and when I tell it to run off the disk, it gives me a bunch of error messages.

The first look something like:

```
[##.######] ata1.00: status: { DRDY ERR }
[##.######] ata1.00: error: { UNC }
[##.######] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[##.######] ata1.00: irq_stat 0x400000008]
```

With the ##'s standing in for various numbers.

Interspered with those error messages I get ones that read:

```
buffer I/O error on device sda, logical block 1
buffer I/O error on device sda, logical block 1
buffer I/O error on device sda, logical block 2
buffer I/O error on device sda, logical block 3
```

etc.

And that's what it's been doing for a while now.  In other words, I can't even get the thing booted up off a live CD anymore.

At this point I've completely mad my peace with never recovering any data of the harddrive -- right now, I'd be thrilled just to get the machine running again.

---

### Post by knidsrok on 2009-04-06
Weird.

So after displaying all those error messages for a (long) while, eventually Ubuntu actually did manage to boot up from the live CD.

So what can I do now?

---

### Post by unutbu on 2009-04-06
knidsrok, I'm sorry to read of your recent troubles.
The error ```


[##.######] ata1.00: status: { DRDY ERR }
```

I believe is an indication that the hard drive is failing.

I think the best thing to do is to try to backup (clone) your hard drive on to another drive of the same or larger size, and if that is successful, then to try to recover data off of the cloned drive.

Instructions on how to use ddrescue can be found here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). 

The same page also explains recovery tools like PhotoRec, which can scan your cloned drive for data files and save them to a new partition or drive. This requires more hard drive space -- unfortunately, there is just no way around that.

The page mentioned above, [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), is the best source I know of for dealing with situations like this.

---

### Post by knidsrok on 2009-04-06
> **unutbu said:**
> knidsrok, I'm sorry to read of your recent troubles.
The error ```


[##.######] ata1.00: status: { DRDY ERR }
```

I believe is an indication that the hard drive is failing.

I think the best thing to do is to try to backup (clone) your hard drive on to another drive of the same or larger size, and if that is successful, then to try to recover data off of the cloned drive.

Instructions on how to use ddrescue can be found here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). 

The same page also explains recovery tools like PhotoRec, which can scan your cloned drive for data files and save them to a new partition or drive. This requires more hard drive space -- unfortunately, there is just no way around that.

The page mentioned above, [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), is the best source I know of for dealing with situations like this.

Yeah, I thought things had gotten pretty bad.

At this point, I'm less interested in recovering any of the data than I am in seeing if I can get the hard drive working again. 

I went to the Western Digital website to download their Data Lifeguard Diagnostics tools, but it seems like they require you to have a machine running Windows even just to create a bootable DOS disk.  

Is there a way to work around this?

---

### Post by rhcm123 on 2009-04-06
> **knidsrok said:**
> Yeah, I thought things had gotten pretty bad.

At this point, I'm less interested in recovering any of the data than I am in seeing if I can get the hard drive working again. 

I went to the Western Digital website to download their Data Lifeguard Diagnostics tools, but it seems like they require you to have a machine running Windows even just to create a bootable DOS disk.  

Is there a way to work around this?

Use wine if you want to stay with ubuntu, or you can buy/torrent/etc a recovery tool. I use r-studio, one of the best $50 i ever spent. it's windows based, but can recover from ext2, ext3, hfs, etc.

---

