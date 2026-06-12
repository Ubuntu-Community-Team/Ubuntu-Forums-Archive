---
title: "UUID not unique anymore..."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Rinzwind on 2009-01-28
After today's update I turned my machine off and now for some reason fsck keeps dying on me. The UUID's inside /etc/fstab have changed BUT what's even weirder is that I have 2 discs with the same UUID. 

After booting up 1 of the discs is not shown here:

 ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-01-28 20:40 19233dcb-6ae3-4b5f-a926-39e1909689c6 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-01-28 20:41 740b0350-af69-4d23-83ec-31b6f6e8b4ce -> ../../sde1
lrwxrwxrwx 1 root root 10 2009-01-28 20:40 7bfd287a-9bab-4ef0-9e35-8931dba74f91 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2009-01-28 20:40 cd79f6ab-6770-4e6c-a4ad-15db909abe02 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-01-28 20:40 cde9bfc0-4c4f-405d-8729-95c0624cd3b3 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-28 20:40 e7041c14-3952-4af6-8d98-fddc8e9313b9 -> ../../sdc1

I miss /dev/sdf1. The command...

 sudo blkid
/dev/sda1: UUID="cde9bfc0-4c4f-405d-8729-95c0624cd3b3" 
/dev/sda2: TYPE="swap" UUID="19233dcb-6ae3-4b5f-a926-39e1909689c6" 
/dev/sdb1: UUID="cd79f6ab-6770-4e6c-a4ad-15db909abe02" 
/dev/sdc1: UUID="e7041c14-3952-4af6-8d98-fddc8e9313b9" 
/dev/sdd1: UUID="7bfd287a-9bab-4ef0-9e35-8931dba74f91" 
/dev/sde1: UUID="740b0350-af69-4d23-83ec-31b6f6e8b4ce" 
/dev/sdf1: UUID="740b0350-af69-4d23-83ec-31b6f6e8b4ce" 

does show it but it has the same UUID as /dev/sde1. WHY? :) 

I found this out searching for uuid en with the help page on ubuntu.
But I can not find a sollution that fixes this. The only thing I found was that a new UUID is created when I format the disc. But that's not an option for me :) 

How do I get another UUID for either /dev/sde1 or /dev/sdf1?

---

### Post by jerome1232 on 2009-01-28
assuming this disc is ext3 or ext2 you can use tune2fs to randomly assign a new uuid

```
sudo tune2fs -U random /dev/sdxx
```


This is the entry in tune2fs man page that I got this command from

```
       -U UUID
              Set the universally unique identifier (UUID) of  the  filesystem
              to UUID.  The format of the UUID is a series of hex digits sepa&#8208;
              rated          by          hyphens,          like          this:
              "c1b9d5a2-f162-11cf-9ece-0020afc76f16".   The UUID parameter may
              also be one of the following:

                   clear  clear the filesystem UUID

                   random generate a new randomly-generated UUID

                   time   generate a new time-based UUID

              The UUID may be used by  mount(8),  fsck(8),  and  /etc/fstab(5)
              (and possibly others) by specifying UUID=uuid instead of a block
              special device name like /dev/hda1.

              See uuidgen(8) for more information.  If  the  system  does  not
              have  a  good  random  number  generator  such as /dev/random or
              /dev/urandom, tune2fs will automatically use a  time-based  UUID
              instead of a randomly-generated UUID.

```

---

### Post by SnakeHips on 2009-01-28
Any clues in here ?
```
cat /etc/fstab
```

Post output if you like i'll take a look.

---

### Post by ByteJuggler on 2009-01-28
Do

```
sudo tune2fs -U random /dev/sda1
```

... replacing sda1 with the partition you need a new uuid for.

---

### Post by Rinzwind on 2009-01-28
Thanks you 3 :) :)
I am now going to do this and report back :)

edit: 
rinzwind@discworldDT:~$ **sudo tune2fs -U random /dev/sdf1**
[sudo] password for rinzwind: 
tune2fs 1.41.3 (12-Oct-2008)
**tune2fs: No such file or directory while trying to open /dev/sdf1**
Couldn't find valid filesystem superblock.
rinzwind@discworldDT:~$ **sudo tune2fs -U random /dev/sde1**
tune2fs 1.41.3 (12-Oct-2008)
rinzwind@discworldDT:~$ sudo blkid
/dev/sda1: UUID="cde9bfc0-4c4f-405d-8729-95c0624cd3b3" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="19233dcb-6ae3-4b5f-a926-39e1909689c6" 
/dev/sdb1: UUID="cd79f6ab-6770-4e6c-a4ad-15db909abe02" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: UUID="e7041c14-3952-4af6-8d98-fddc8e9313b9" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdd1: UUID="7bfd287a-9bab-4ef0-9e35-8931dba74f91" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sde1: UUID="0af8f6d9-bdbd-40cd-bcab-26f3c3b2d274" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdf1: UUID="740b0350-af69-4d23-83ec-31b6f6e8b4ce" TYPE="ext3" SEC_TYPE="ext2" 
rinzwind@discworldDT:~$ 

damn that was way to easy :)
I am still a n00b it seemms :D

---

