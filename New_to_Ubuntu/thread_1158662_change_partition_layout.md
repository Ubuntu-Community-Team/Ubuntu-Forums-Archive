---
title: "change partition layout"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Linux&amp;Gsus on 2009-05-13
Hi all.
I have a machine here that looks like this:
```
Disk /dev/sda: 749.6 GB, 749606010880 bytes
255 heads, 63 sectors/track, 91134 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10         271     2104515    c  W95 FAT32 (LBA)
/dev/sda3             272        1487     9767520   83  Linux
/dev/sda4            1488       91134   720089527+   5  Extended
/dev/sda5           91013       91134      979965   82  Linux swap / Solaris
/dev/sda6            1488       91011   719101467   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3748.0 GB, 3748030054400 bytes
255 heads, 63 sectors/track, 455672 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147483647+  ee  EFI GPT
```

On /dev/sda is root, home and swap, /dev/sdb is for backups only and therefore not to be touched.
However, on /home is pretty much all empty and I would like to shrink that down and add another partition for /var. New install isn't really an option.

Is it possible to change the partition layout like this? I assume it would something like a GParted LiveCD, right?
But then how do I do it, /var needs to be mounted at boot time, of course, and also the current directory needs to be transfered. Can that be done without breaking the system?

Thanks for any help.
L&G

---

### Post by Ericyzfr1 on 2009-05-13
You should be able to shrink your /home partition with Gparted LiveCD. However, regarding creating a /var.....I never tried it.

---

### Post by -kg- on 2009-05-13
If you need to create a /var partition, GPartEd will do that once you shrink your /home, assuming that sda6 is your /home partition.  Just shrink sda6 down and create your /var partition, formatting it to your desired filesystem format.

If, however, your /home partition is sda3, you're SOL as far as doing this easily, the way you have your partitions set up.  Since you already have 4 Primary partitions (sda1 - sda3 plus the Extended partition, which is a special type of Primary partition makes 4), you would have to delete one of those partitions, extend the Extended partition into it, and then you would be able to create your partition (and re-create the partition you had to get rid of, for that matter) inside of it.

Please see [How To Partition]("https://help.ubuntu.com/community/HowtoPartition") in the Community Wiki for a more comprehensive explanation, with screen shots and everything.

---

### Post by Linux&amp;Gsus on 2009-05-13
Thanks lots for the quick replies.

sda3 is / (ext3)
sda4 is extended - don't really know what it's doing there
sda5 is swap
sda6 is /home - pretty big and almost empty (ext3)

It's not my machine, so I really need to know what I'm doing there and that it works/is possible to do. When you see my head rolling around the floor you can cancel my account here... :lol:
Will read through the link, thanks for that one.

Cheers,
L&G

---

### Post by quixote on 2009-05-14
If I had to guess, sda6 is probably /home ?  and it seems to take up all of the extended partition ....

Okay, I see your more recent answer, and that's indeed the case.  In that case I think it may be somewhat simple.  As others said, use gparted to use some of the space from home to create a new logical partition.  I'll assume you're using the default ext3 filesystem.

Use ```
sudo cp -a /var/* /dev/sda7/whatever-you've-called-your-new-partition
```.  -a will preserve all the permissions and so on of the files.  (Initially, don't erase or move those files.  Then you can go back to the way things were if it doesn't work.)

Then mount your new partition on /var
```
sudo mount -t ext3 /dev/sda7/new-partition /var
```

While it's mounted, the operating system will see only the new contents of /var.  If it's not mounted, your old ordinary /var will still be right there.

Okay: now a couple of questions:  why do you want a separate partition for /var?  I could understand /usr, because then the programs you install have a better chance of staying put through upgrades to new OS versions.  But why /var? ??

If this isn't your machine, maybe you better do a dry run on your own machine first?  This is some rather major stuff you're proposing to do to this person's system.  How upset will they be if there's a problem? ;)

---

### Post by louieb on 2009-05-14
Just look around for a how to on creating a separate /home. The [Psychocats]("http://www.psychocats.net/ubuntu/index.php")  link in signature has that how to. Same steps your just moving a separate branch of the file-system.  

Just wondering why - don't see much benefit putting /var on a separate partition in a desktop PC.

---

### Post by Linux&amp;Gsus on 2009-05-14
Thanks for the replies, guys.

Well, it's not a desktop. This machine is a server and so far used for backups. The wish is to extend the servers use with some groupware and knowledgebase kinda software (most likely a wiki).
Since these are web based apps I believe they install into /var. Unless I mixing something up here there would be (over time) space needed for /var then what is available under /
Also, I thought it would be better to  therefore create a separate partition for that, rather then shrinking /home and increasing /

If my thinking is wrong please feel free to correct me and suggest a better solution. Of course, I prefer the easiest possible way. ;)


Thanks again for the help.
L&G

---

### Post by quixote on 2009-05-15
I don't know about *wrong*, exactly.  A bit nontraditional perhaps.  You're right that the default for web things is /var/www (but not just plain /var).  Depending how big and how critical the web sites are, I can see wanting that on a separate partition.  The nicest thing about it is that if another partition gets fried, it doesn't affect the /var/www

Anyway, good luck, and do try it first on a non-critical system ;-)

---

