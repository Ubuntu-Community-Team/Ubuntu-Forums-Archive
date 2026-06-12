---
title: "Creative use for unallocated space?"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by steve7777777 on 2011-01-05
I have some SMART errors on my sd1 drive so am replacing it. The old drive is 320 gb and the new drive is 500 gb. I use ext4. After restoring an image made with Clonezilla there is ~180GB of unallocated space. From what I understand, I can use  

resize2fs -p /dev/sda2

to grow the partition where sda2 is the partition that needs to be increased in size. 

I don't need more than 320 gb for the sda2. 

Question - before I grow the partition, are there any suggestions for using this unallocated space? I assume an alternative is also to leave it unallocated for now. The PC is Ubuntu only, and I use VM for playing around with other distros, so dual boot not needed.

Thanks!

---

### Post by seawolf167 on 2011-01-05
You can build your own system following [URL="http://www.linuxfromscratch.org/"]Linux From Scratch
[/URL]
Otherwise I'd just use gparted and resize, its not like you can't resize again later if you think of a use

---

### Post by MartyBuntu on 2011-01-05
I just wish gparted had a **merge** option, where you can join two similarly formatted partitions. I've never been able to do that.

To the OP...you can always format the unallocated space and use it for extra storage space.

---

### Post by steve7777777 on 2011-01-05
> **seawolf167 said:**
> ...just use gparted and resize, its not like you can't resize again later if you think of a use

Am I missing something? It seams easier to boot a live CD and run 

resize2fs -p /dev/sda2

from the command line as opposed to Gparted.

---

### Post by blind2314 on 2011-01-05
No..it's not really any easier, you're booting off a CD either way. But it's your preference.

---

### Post by psusi on 2011-01-05
> **steve7777777 said:**
> Am I missing something? It seams easier to boot a live CD and run 

resize2fs -p /dev/sda2

from the command line as opposed to Gparted.

You also need to fiddle with fdisk to enlarge the partition first, then resize2fs.  That's why it is easier to use gparted.

---

### Post by anystupidname1 on 2011-01-05
Perfect opportunity to mess around with btrfs :)

---

