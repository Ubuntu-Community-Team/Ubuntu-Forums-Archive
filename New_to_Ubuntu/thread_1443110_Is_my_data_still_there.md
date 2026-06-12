---
title: "Is my data still there?"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by raceon4 on 2010-03-30
Recently had an issue where my computer would not boot.  Was able to create a live USB stick and disk utility says that the SSD is still in fine shape.

My question is is there anyway to get the data that I had on that drive off of the SSD or is it lost permanently and I just need to do a new install?

---

### Post by halitech on 2010-03-30
if the drive is fine then you should be able to mount the drive and copy/move the data to another drive

---

### Post by raceon4 on 2010-03-30
This may sound dumb but how exactly would I go about doing that?

---

### Post by raceon4 on 2010-03-30
When I go to disk utility to mount the drive the only option is erase.  Everything else is grayed out.

---

### Post by halitech on 2010-03-30
look under places and see if the drive is listed. if its not, open a terminal and run
```
sudo fdisk -l
```
post the info back here

---

### Post by Rex Bouwense on 2010-03-30
Your data probably is still there.  Can you use the flash drive to boot?  If you can you should be able to get to your desk top.  Alternatively, can you boot from any kernal?

My slow typing skills have made this post OBE.

---

### Post by The Real Dave on 2010-03-30
If everythings ok, you should be able to mount the drive and copy your data. What do you see in the Places menu?

---

### Post by raceon4 on 2010-03-30
Disk /dev/sda: 15.4 GB, 15408046080 bytes
255 heads, 63 sectors/track, 1873 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47c3cd47

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 2002 MB, 2002747392 bytes
16 heads, 32 sectors/track, 7639 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x41f03319

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16        7640     1951808    b  W95 FAT32

---

### Post by halitech on 2010-03-30
looks like your main drive is a 15gig drive?

[color="red"]Disk /dev/sda doesn't contain a valid partition table[/color]

this doesn't look good to me

---

### Post by The Real Dave on 2010-03-30
Looks like you'll need to use Testdisk to restore your partition table, assuming the 15Gb drive is your SDD
[URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]
Guide[/URL]

---

### Post by raceon4 on 2010-03-30
Yea it should be a 16GB drive.  

ATA STEC PATA 16GB is what Diskutility says.

It also says not partitioned as well.

It does not show up at all in places.

---

### Post by The Real Dave on 2010-03-30
Ok, your partition table has been erased. You may be able to get your data back, some at least. Try not to access the disk, don't go running any checks like, or you'll probably erase your data. Follow the guide I mentioned previously, which will walk you through recovering your partition table.

To install test disk in Ubuntu, open Synaptic, or type in a terminal [Applications>Accessories>Terminal] 

```
sudo apt-get install testdisk
```

You can also use a LiveCD such as PartedMagic, which will already have testdisk installed.

---

### Post by raceon4 on 2010-03-30
Thanks will try that and see what happens.

---

### Post by The Real Dave on 2010-03-30
Best of Luck :)

---

### Post by raceon4 on 2010-03-30
I can't seem to find it in synaptic and running the command in terminal doesn't amount to anything.

---

### Post by The Real Dave on 2010-03-30
You're probably best off to download [Parted Magic]("http://partedmagic.com/"), run that LiveCD and use testdisk from there.

---

### Post by raceon4 on 2010-03-30
Ok I added the other repositories and was able to find it so lets see what happens.

---

### Post by raceon4 on 2010-03-30
So I found the partitions that looked right according to the drive when I boot from the stick and go to load the filesystem this is the error I get.

Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by J V on 2010-03-30
iirc you can't install anything on a live disc, so you should burn a testdisk, until you do this you can't get your data back

---

### Post by raceon4 on 2010-03-30
Sorry but I really have no idea what that means.

---

### Post by The Real Dave on 2010-03-30
Your superblock is corrupt :( Today just ain't your day. 

Find where the superblock backups are stored on your drive with

```
sudo mke2fs -n /dev/sda5
```

It should give back something like

```
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208

```

Take the first value, and run

```
sudo e2fsck -b block_number /dev/sda5
```

EDIT: Guide can be found on my blog, [here]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/").

---

### Post by raceon4 on 2010-03-30
Is it possible to put this on a flash drive?  I do not have a cd drive on my netbook.

---

### Post by The Real Dave on 2010-03-31
Maybe [Unetbootin]("http://unetbootin.sourceforge.net/") will work?

---

### Post by raceon4 on 2010-05-05
So I was able to run the codes you mentioned and I get this error when trying to restore the superblock


This was the first time I tried one of the backups

ubuntu@ubuntu:~$ sudo e2fsck -b 32678 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


The second

ubuntu@ubuntu:~$ sudo e2fsck -b 98304 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda5: recovering journal

Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
e2fsck: unable to set superblock flags on /dev/sda5

The third

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo e2fsck -b 163840 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda5: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
e2fsck: unable to set superblock flags on /dev/sda5



Any thoughts?  If the data is truly gone I might as well just do a clean install to get things back to normal right?

---

### Post by raceon4 on 2010-05-15
Just bumping this up to see if anyone might be able to help.

---

### Post by The Real Dave on 2010-05-21
> **raceon4 said:**
> Just bumping this up to see if anyone might be able to help.

Try changing the command to 

```
sudo e2fsck -p -b 98304 /dev/sda5 
```

The -p option should attempt to auto repair problems with the filesystem. I've not tried this, just working on what I found in Google, so no warranty ;)

I hope this works for you mate. 

[Source]("http://kubuntuforums.net/forums/index.php?topic=3105200.0")

---

### Post by raceon4 on 2010-05-21
Thanks for the quick reply.  Here's what happened.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo e2fsck -p -b 98304 /dev/sda5
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda5: recovering journal
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Recovery flag not set in backup superblock, so running journal anyway.
e2fsck: unable to set superblock flags on /dev/sda5

ubuntu@ubuntu:~$ 

any ideas?

---

### Post by The Real Dave on 2010-05-22
> **raceon4 said:**
> Thanks for the quick reply.  Here's what happened.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo e2fsck -p -b 98304 /dev/sda5
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda5: recovering journal
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Recovery flag not set in backup superblock, so running journal anyway.
e2fsck: unable to set superblock flags on /dev/sda5

ubuntu@ubuntu:~$ 

any ideas?


Hmmm, again stabbing in the dark here, but try 

```
sudo e2fsck -p /dev/sda5
```

or 

```
sudo fsck.ext4 -a /dev/sda5
```

Both should attempt to repair the filesystem without reference to the superblock

---

### Post by raceon4 on 2010-05-22
Here's what I got.


ubuntu@ubuntu:~$ sudo e2fsck -p /dva/sda5
e2fsck: No such file or directory while trying to open /dva/sda5
/dva/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck.ext4 -a /dva/sda5
fsck.ext4: No such file or directory while trying to open /dva/sda5
/dva/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by da burger on 2010-05-22
I know nothing about this kind of thing but from your last out put it looks like there is a typo. Try replacing /dva/sda5 with /dev/sda5.

---

### Post by raceon4 on 2010-05-22
With they typos fixed here is the readout

ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sda5
/dev/sda5: recovering journal
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Run journal anyway

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$ sudo fsck.ext4 -a /dev/sda5
/dev/sda5: recovering journal
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Run journal anyway

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

---

### Post by The Real Dave on 2010-05-22
> **raceon4 said:**
> Here's what I got.


ubuntu@ubuntu:~$ sudo e2fsck -p /dva/sda5
e2fsck: No such file or directory while trying to open /dva/sda5
/dva/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck.ext4 -a /dva/sda5
fsck.ext4: No such file or directory while trying to open /dva/sda5
/dva/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

You've made a typo in the command mate it's /dev/ not /dva/

---

### Post by The Real Dave on 2010-05-22
> **raceon4 said:**
> With they typos fixed here is the readout

ubuntu@ubuntu:~$ sudo e2fsck -p /dev/sda5
/dev/sda5: recovering journal
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Run journal anyway

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$ sudo fsck.ext4 -a /dev/sda5
/dev/sda5: recovering journal
/dev/sda5: Superblock needs_recovery flag is clear, but journal has data.
/dev/sda5: Run journal anyway

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

Ok, it doesn't want to do it automatically.

Run

```
sudo fsck.ext4 -r /dev/sda5
```

and it'll probably show you some problems, and ask to fix them. Unless it looks strange, or warns of danger, hit y to accept.

---

### Post by bcbc on 2010-05-22
> **The Real Dave said:**
> Ok, it doesn't want to do it automatically.

Run

```
sudo fsck.ext4 -r /dev/sda5
```

and it'll probably show you some problems, and ask to fix them. Unless it looks strange, or warns of danger, hit y to accept.

Have you thought about using photorec to recover the data (in readonly mode) before taking corrective action that could lose data.

---

### Post by The Real Dave on 2010-05-22
> **bcbc said:**
> Have you thought about using photorec to recover the data (in readonly mode) before taking corrective action that could lose data.

I hadn't tbh. I have no experience with that.

---

### Post by bcbc on 2010-05-22
Well after reading the thread ;) I see that the OP had trouble installing and running testdisk so this may be an obstacle.

But anyway - if the data is important enough it might be worth it to wait and figure it out, or get someone to help do this (like at a computer shop).

---

### Post by The Real Dave on 2010-05-22
> **bcbc said:**
> Well after reading the thread ;) I see that the OP had trouble installing and running testdisk so this may be an obstacle.

But anyway - if the data is important enough it might be worth it to wait and figure it out, or get someone to help do this (like at a computer shop).

Good point mate, and good advice :)

---

### Post by HotShotDJ on 2010-05-22
> **bcbc said:**
> But anyway - if the data is important enough it might be worth it to wait and figure it out, or get someone to help do this (like at a computer shop).A agree.  Testdisk is THE tool for this, and from personal experience, it works nearly flawlessly for recovering data.  I fear that all this flailing about trying to use anything BUT testdisk may have made the situation worse for the OP.

I'm sure that one could use Unetbootin to create bootable USB drives (it is worth taking the time to learn how -- install it via Synaptic Package Manager) and then run TestDisk from there.  My favorite distribution for system recovery is [RIPLinux]("http://www.tux.org/pub/people/kent-robotti/looplinux/rip/").

---

### Post by raceon4 on 2010-05-22
I actually was able to get Testdisk installed and used that to recover the partitions in the first place.  Is there something else that I should have done?

---

### Post by bcbc on 2010-05-22
> **raceon4 said:**
> I actually was able to get Testdisk installed and used that to recover the partitions in the first place.  Is there something else that I should have done?

OK if you can run testdisk, you can run photorec (it comes with testdisk).

So I ran it on a partition to test it, but you can run it on a drive... in the following example, I am assuming you have mounted an external usb and created a directory called photorec to hold the recovered data. 

```
sudo photorec /d */media/externalusb/photorec/* /dev/sda
```

Then select 
Proceed
Select partition table type (Intel for me, as per default)
Select the partition to recover
Select file system (whatever it was)
Select Whole to get everything

Then go away for the weekend (just kidding, but I guess it takes a while). Make sure you have enough room under the */media/externalusb* to save the files.

Caveat - I haven't had to run this for data recovery, but I let it run a little and it was pulling off my data. I recommend reading the manual and familiarising yourself with it first.

Edit: I don't think the file names are very meaningful f0123456.jpg, but I guess it's better than nothing.


EDIT: Use this guide instead of my ramblings [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

