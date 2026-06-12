---
title: "removing vista completely without losing data &amp; use the remaining space in ubuntu?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by fuser312 on 2009-01-16
ok i have a 250 gb hdd with ubuntu sharing 50 gb. but i am done with vista & i want to completely remove it and give all space to ubuntu(or may be install other distros). but i want to save some files of mine around 80 gb. i have no external hdd to make a back up. so is there any way out. please see.

---

### Post by lswest on 2009-01-16
I would resize the windows partition from your Ubuntu LiveCD, then make the Ubuntu partition large enough to hold all the files.  Once you've copied the files over, delete the windows partition (again, from the LiveCD) and give the remaining space to your Ubuntu install.

---

### Post by northern lights on 2009-01-16
- Free up as much space on the Vista partition as you can.
- Resize the Vista partition as small as it can get (i.e. with hardly any free space left).
- Either create a new partition in the unallocated space or add the unallocated space to the Ubuntu partition.
- Move data.
- Repeat if necessary.

As an aside, you might want to consider more than one partition. A separate /home and/or a standalone data partition can be handy when reinstalling the system or for sharing between OSs/distros.

---

### Post by fuser312 on 2009-01-16
i have only 1 drive in vista with 13 gb left and shrinking is not working somehow

could you explain a little more about live cd method

---

### Post by northern lights on 2009-01-16
> **fuser312 said:**
> could you explain a little more about live cd methodWhether from the LiveCD or an installed Ubuntu, run```
gksu gparted
```
and use the partitioner.

---

### Post by redseventyseven on 2009-01-16
Ahem.
[http://ubuntuforums.org/showthread.php?t=1041122](http://ubuntuforums.org/showthread.php?t=1041122)
Please don't start more than one topic for the same issue. It's such a waste of time to answer a query in one topic only to find that someone else has made exactly the same answer in another. Thanks!

---

### Post by fuser312 on 2009-01-16
gksu gparted

nothing happen after running this command, it just asked for the password and when i provided it, nothing happened


and hey sorry for double post, it was not intended.
one was meant for other forum, but unknowingly i posted twice here

---

### Post by fuser312 on 2009-01-16
ben as i told i have only one partition in vista and shrinking is not working somehow, also i already have ubuntu installed, i just want to get more space to it.

---

### Post by Ben Page on 2009-01-16
I don't understand, how many partitions do you have? Do you have only one 250GB partition? Can you explain it more if you have more virtual partitions?

---

### Post by fuser312 on 2009-01-16
> You can leave your data partiton as it is in NTFS filesystem

i have only one partition in vista c:\ no separate partition for data

---

### Post by Ben Page on 2009-01-16
Ah..so you can resize it, say 30 GBs dedicated to Ubuntu. You can do this by downloading the Partition Magic app. It is he best app for partitioning (for windows). Resize the "c:\" partition to 250 - 30 gbs, it will take a while, and then make 30 gbs ext3 partition in the "unallocated" space. You can also make a swap partition (linux swap 1-2 GBs).Install Ubuntu to 30GB partition. Then you just delete Vista files from your resized 220GB partition and there you go - you will have Ubuntu only machine.
All this can be done in Linux partitioner, but it is a little more complicated, and Linux won't hesitate to wipe out your whole disk - so be careful. You have to select manual partitioning when installing linux.

---

### Post by fuser312 on 2009-01-16
i have ubuntu installed, i don't need and want to install it again. the gist of question is how could i use the remaining windows space in ubuntu without a fresh install. ok i will format it to ext3 but how could i add that to the existing ubuntu installation

---

### Post by Ben Page on 2009-01-16
But where and how did you install Ubuntu? Are windows and Ubuntu systems in the same partition? If so, just delete Windows installation from Ubuntu, but I don't understand how can Ubuntu be installed into NTFS file system, are you using WUBI?

---

### Post by fuser312 on 2009-01-16
of course ubuntu is installed on other parttion.
haven't you read my posts. 50 gb linux and remaining with vista

anyways i appreciate your efforts

---

### Post by Ben Page on 2009-01-16
So, its an easy thing, just delete Vista files, and there is your free space! And you got rid of Vista, just pay attenyion where is your GRUB (dont delete it).

---

### Post by fuser312 on 2009-01-16
take that space automatically. where and how will it place this space in file structure

---

### Post by fuser312 on 2009-01-16
but again there should be no problem if i want to use some space from it for other linux distros

---

