---
title: "Can't find my D: drive"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by iguanaboy on 2009-10-19
Hello,

I have just installed Ubuntu 9.0.4 on my laptop; but before doing that, I had moved all my data to my D: drive. Ubuntu is working fine, but I don't know how to access my D: drive! Can anybody help?

Thanks!

---

### Post by Peter09 on 2009-10-19
In Ubuntu Drives are not allocated letters like in windows. They are mounted onto existing folders, click the folder and inside you find the contents of your drive.

Try looking in the Places menu - top left- for the drive.

---

### Post by samigina on 2009-10-19
Is a ntfs partition?

In linux the partition names are not letters like in windows, if you open your Computer you will see all your partitions named by thedrive capacity.

---

### Post by philinux on 2009-10-19
> **iguanaboy said:**
> Hello,

I have just installed Ubuntu 9.0.4 on my laptop; but before doing that, I had moved all my data to my D: drive. Ubuntu is working fine, but I don't know how to access my D: drive! Can anybody help?

Thanks!

Look under Places top left on Desktop.

Is this a dual boot or wubi install? If wubi look under Places>FileSystem>Media.

---

### Post by iguanaboy on 2009-10-19
Thanks for the replies, but I still haven't found it. I installed Ubuntu using a CD I had downloaded. I have looked in all the folders available in my Places, but all were empty.

---

### Post by jwbrase on 2009-10-19
> **iguanaboy said:**
> Hello,

I have just installed Ubuntu 9.0.4 on my laptop; but before doing that, I had moved all my data to my D: drive. Ubuntu is working fine, but I don't know how to access my D: drive! Can anybody help?

Thanks!

"D:" is just the name that Windows uses for that particular drive. You won't find it under that name because that's a drive naming scheme that only Windows uses (plus some older related OS's like DOS).

Look under Places -> Computer, and it should appear as something like "xxx GB Volume", with "xxx" being the size of the drive in gigabytes.

---

### Post by iguanaboy on 2009-10-19
My "Computer" has only two items: my CD/DVD Drive and Filesystem. Filesystem has a bunch of 3-letter names but nothing like the xxx GB Volume you describe.

---

### Post by philinux on 2009-10-19
> **iguanaboy said:**
> My "Computer" has only two items: my CD/DVD Drive and Filesystem. Filesystem has a bunch of 3-letter names but nothing like the xxx GB Volume you describe.

Is this a pc with one hard drive and did you tell the installer to use all the disk. In which case windows could have gone byebye. Just to check.

Open a terminal Apps>accessories>terminal and use this command. Copy and paste it.

```
sudo fdisk -l
```

Post back the result.

Like I said before did you use wubi? In which case.

Places>File System the look in the media folder.

> Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.

---

### Post by iguanaboy on 2009-10-19
My Laptop had 2 drives, a C: and a D:. Windows was in the C: and got erased when I installed Ubuntu with the CD (not wubu). But all my data was stored in D:, and I am trying to get it back. Is it doable?

---

### Post by -Zeus- on 2009-10-19
Please post the output of the following commands:

```
less /etc/fstab
less /etc/mtab
sudo fdisk -l
df -h
```

---

### Post by Peter09 on 2009-10-19
As Philinux said please post the output of

```
sudo fdisk -l
```

---

### Post by LewRockwell on 2009-10-19
> **iguanaboy said:**
> My Laptop had 2 drives, a C: and a D:. Windows was in the C: and got erased when I installed Ubuntu with the CD (not wubu). But all my data was stored in D:, and I am trying to get it back. Is it doable?

It's possible that you have misunderstood your laptop's hardware and how it is/was set up

Most laptops have one internal hard drive

Many of these laptops come with Windows Operating System on the "C" partition of the hard drive...and a restore/data/archive partition usually designated as "D" partition...you'll note that BOTH of these partitions are located on the single internal hard drive in your laptop

So if you told the ubuntu installer to use the whole internal hard drive then you have most likely reformated and written over some of your previous windows installation and/or your backup/data/archive information

hopefully you have back-ups/clones/off-drive-safe-storage/etc. of anything of value...

if not then there is a slight chance that you might recover stuff that wasn't written-over

you'd be using something like Photorec which is on the Parted Magic LiveCD Utilities Disk

[http://partedmagic.com/](http://partedmagic.com/)

.

---

### Post by egalvan on 2009-10-19
> **LewRockwell said:**
> It's possible that you have misunderstood your laptop's hardware and how it is/was set up

Most laptops have one internal hard drive

hopefully you have back-ups/clones/off-drive-safe-storage/etc. of anything of value...

if not then there is a slight chance that you might recover stuff that wasn't written-over

you'd be using something like Photorec which is on the Parted Magic LiveCD Utilities Disk

[http://partedmagic.com/](http://partedmagic.com/)

.

Hey Lou, +1 +1 for Parted Magic LiveCD

Also, if the OP has only one drive, and it was partitioned into two,
then depending on the size of the first partition (C: or Windows drive),
then he has a good chance of recovering most all of his info on the second partition.

The bigger the first partition, the further away from the start of the drive the second partition is,
and the further the data was from the Linux partitions...

Second, since he *moved* his data to the second partition, it most likely was highly contiguous.
This also raises the probabilities of a good data recovery.

And then, just to raise his hopes a little....

I had a client whose husband re-installed XP on her machine she used for school work...
 (the machine had slowed down, so he thought the re-install would help... poor man)
She lost six months of assignments and her thesis.
TWO MONTHS after this, they hired me to try to recover her school work. They had  used the machine daily.

I used Parted Magic and managed to recover ALL her school work,
and about 90% of the pictures she had.
Only about a fourth of the music, but she did not care about that.

You Mileage WILL Vary, but don't loose hope just yet...

Thanks Lou.


P.S.

consider a donation to the PartedMagic authors.
even $2 will make a difference.
Imagine what this would cost in the Windows World.

I am on a $2-a-month subscription.
It's worth every penny.
Cheers

---

### Post by iguanaboy on 2009-10-19
All right, so from reading the comments I guess I have just erased my D:. Major letdown! Anyway, when I type sudo fdisk -1, I get:

fdisk: invalid option - - '1'

and some other stuff, but I guess that what this tells me is that it couldn't find the disk?

---

### Post by Excedio on 2009-10-19
> **iguanaboy said:**
> All right, so from reading the comments I guess I have just erased my D:. Major letdown! Anyway, when I type sudo fdisk -1, I get:
 
fdisk: invalid option - - '1'
 
and some other stuff, but I guess that what this tells me is that it couldn't find the disk?
 
```
sudo fdisk -l
```
 
That's a letter L not a number 1.

---

### Post by p0cky84 on 2009-10-19
If your D: drive had a label, such as "backup" or "games", do a ```
ls /dev/disk/by-label
```
else you can do a ```
ls /dev/disk/by-{id,path,uuid}
```

---

### Post by iguanaboy on 2009-10-19
OK, I did the sudo fdisk -l thing, and it tells me I have 3 devices: /dev/sda1, /dev/sda2, /dev/sda3/ and some other information. Which information is relevant to my problem?

---

### Post by b0b138 on 2009-10-19
all of it. copy and paste the entire output

---

### Post by iguanaboy on 2009-10-19
Here's what I get:


Device  Boot  Start    End    Blocks    Id   System
/dev/sda1 *       1  18706  150255913+  83   Linux
/dev/sda2     18707  19457    6032407+   5   Extended
/dev/sda2     18707  19457    6032376   82   Linux swap / Solaris

---

### Post by surfed on 2009-10-19
You told the installer to use the entire disk during install. It erased your "D" drive. You just learned a valuble lesson in backing up your data. Do not pass go.

---

### Post by iguanaboy on 2009-10-19
Hmmmkay, is there any way to get some of my data back besides using the partedmagic CD?

---

### Post by surfed on 2009-10-19
At this stage, No. Not even partitionmagic is gonna help.

---

### Post by egalvan on 2009-10-19
> **iguanaboy said:**
> All right, so from reading the comments I guess I have just erased my D:. Major letdown!


Again, you may, or may not, have "erased" your D: drive.

You need to use other tools to try to access the information.

Testdisk from the PartedMagic LiveCD is one excellent method.

---

### Post by cabrey on 2009-10-19
> **surfed said:**
> At this stage, No. Not even partitionmagic is gonna help.

Uhhh yes it will. That's the point of the software, to recover data (and other rescue stuff). :confused:

---

### Post by surfed on 2009-10-19
If its a 160gb drive than he has not much hope. According to his fstab he has one root partition and one swap. The swap is at the end of the drive, if his system has swaped at all then his data is at least corrupted as they will have been overwritten, then again it depends on how big his "D" was, he might be lucky, i am curious to see. But then sending him out to do data recovery with P-Magic after not having fully understood disk partitioning in the first place does not raise my hopes much. Give it a shot but do read the documentation first and think 3 times before doing anything.

---

### Post by iguanaboy on 2009-10-19
Thanks mates, I'll keep you updated.

---

