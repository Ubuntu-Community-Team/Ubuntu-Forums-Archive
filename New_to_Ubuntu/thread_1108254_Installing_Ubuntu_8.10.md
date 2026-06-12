---
title: "Installing Ubuntu 8.10"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Meatspin on 2009-03-27
ok I did a search on this, but couldn't find my exact issue. 

My Case is..

I have a 100GB harddrive and it was prepartiioned into 2 seperate drives. The first one is the C drive which contains my current Windows XP operating system and the second one was a recovery drive D which curretnly has nothing on it. I want to install Ubuntu 8.10 onto the drive D since it is curretnly not in use and would like to dual boot. When trying to configure the partitions when installing ubuntu, it allows me a guided feature which would split my C into two parts 30 some percent for xp and the rest of ubuntu. The second option is the whole (100GB) drive and the last one is manual. I tried using manual to install it, but I get errors something roots not defined? I'm not sure if i am appoching this correctly.. any help would be apperciated thanks.

---

### Post by drs305 on 2009-03-27
When you select to manually partition the drive there are a couple of steps. First you must select the partition. Next you must designate it as /. You click on a drop down list and there are a range of system partitions to select from. You must select / for one of the partitions (your main install partition). Even though swap files are now possible, I *believe* you still have to designate a second small (1-4GB) partition as a swap partition, which you also have to designate via the drop down menu.

---

### Post by Xero Xenith on 2009-03-27
Hello tharr :)

Something you should know first of all is that the "names" you refer to (C and D) are exclusive to Windows, and they aren't named like that anywhere else at all. What I think you're trying to say is that you have your root Windows drive (C) and another partition (D) that you want to erase: or have you erased it already?

A direct solution to the "Root not defined" problem would be that you haven't assigned a root partition in the partitioner. This can be done by selecting a partition, then changing the Mountpoint to "/" (no quotes).

However, it would be much more helpful if you could tell us exactly how it's partitioned at the moment, and excactly what you're trying to achieve. Then we can give advice as appropriate :)

-X

EDIT: beat to the punch :P however, one small correction: you don't *have* to make a swap partition, but it is strongly recommended. Again, if you tell us exactly how it is at the moment and exactly what you want to achieve, we can advise as appropriate.

---

### Post by Meatspin on 2009-03-27
Hm well curretnly I only have windows xp installed. There are 2 partitions, one being C my harddrive with my windows xp operating system installed. The second partition is D which was initially a recovery partition preinstalled on the computer when I got it. Currently partition D has nothing on it, I would like to designate partition D to install ubuntu on it, and being able to leave my windows xp exactly the way it is and dual boot with ubuntu installed. I need some step by step instructions on how to do this via manual mode. any help is apperciated thanks. I am also still kind of confused with the root error thingy can someone elaborate on that.

---

### Post by drs305 on 2009-03-27
Here is a link to a guide for setting up intrepid. It has graphics of the partitioning process which you will probably find helpful:
[http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install]("http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install")

Instead of C and D drives, as Xero Xenith stated, linux refers to them as sdXX, with the first X being a letter and the second being a partition number ( sda1, sdb1, sdb2, etc). Your windows partition is probably sda1 and you will *probably* be working with sdb. Make sure you know before formatting the drive!

---

### Post by mlentink on 2009-03-27
Terminology.

Unfortunately, coming from a windows world, you are used to its own lingo.

Think of a (physical) disk drive as a cake. You can split it many ways. In our world, a disk can only be split into 4 chunks, but they do not need to be of equal size. Those chunks are called partitions. As far as I know, Windows is the only OS that actually calls them 'disks', which of course they aren't (they are only parts of a disk). Many times you need more chunks. In that case, one of the four primary chunks is magically transformed into a new 'cake', say a virtual cake, which can be further divided in many 'logical' chunks. 

Your physical disk has two chunks, or (try to get used to the terminology) partitions. One devoted to Windows, formatted with the NTFS filesystem, and another one which the manufacturer (HP?) formatted to allow you to restore your system to factory defaults.

The question is: in order to successfully install Ubuntu, how big is that second partition? The Ubuntu installer will tell you. 

But before you do anything to partitions: back up your data. Make sure you have backed up your data. Defragment your windows partition (your 'C: -drive'), defragment it again. Then defragment it a third time.

Then, and only then, you can start shrinking the size of your windows partition, making the other partition bigger and installing ubuntu.


Afterthought: why bother? Ubuntu is far superior, so back up your files, and let ubuntu take the whole disk. You're going to want that in a year or so anyway

---

### Post by perrti-y02 on 2009-03-27
One thing to add to mlentink's fantastic analogy is make sure you know which partition has Windoze on it. Try booting into the live CD and comparing the sizes of partitions to establish which is which. I apologise if you have already done this but I have made the mistake before.

---

### Post by Meatspin on 2009-03-27
I forgot to mention the partion I'm planning to install on is pretty much split half and half. 40 some gigs is the primary drive with windows on it and the other recovery one(from acer) is roughly the same size and is completlely empty. So would I need to have windows installed in the partition I want to install ubuntu as well before I can dual boot?

---

### Post by drs305 on 2009-03-27
No, they don't have to be on the same partition. In fact, they can't be as they both require their own format - ntfs for windows and ext2/3/4 for ubuntu (ext3 is normal).

By the way, I just noticed your post number. Welcome to the ubuntu forums!

---

### Post by mlentink on 2009-03-27
> **Meatspin said:**
> I forgot to mention the partion I'm planning to install on is pretty much split half and half. 40 some gigs is the primary drive with windows on it and the other recovery one(from acer) is roughly the same size and is completlely empty. So would I need to have windows installed in the partition I want to install ubuntu as well before I can dual boot?
Good news!

40 Gigs is more than enough for Ubuntu.
What we need to do now is to delete the partition which you call your ´D:-drive', and in its place create other partitions. My personal preference would be to create three partitions (two more primary partitions and one extended.)

I would create:
a partition formatted with the ext3 filesystem, as system partition '/', 8 GB is fine
a partition formatted with the ext3 filesystem, as data partition '/home', 31 GB
a logical partition formatted as linux/swap, 1 GB is enough

---

### Post by Meatspin on 2009-03-27
ok thanks everyone. I will experiement more with this tonight and ask for more help if needed. Thanks everyone once again.

---

### Post by presence1960 on 2009-03-27
> **Meatspin said:**
> Hm well curretnly I only have windows xp installed. There are 2 partitions, one being C my harddrive with my windows xp operating system installed. The second partition is D which was initially a recovery partition preinstalled on the computer when I got it. Currently partition D has nothing on it, I would like to designate partition D to install ubuntu on it, and being able to leave my windows xp exactly the way it is and dual boot with ubuntu installed. I need some step by step instructions on how to do this via manual mode. any help is apperciated thanks. I am also still kind of confused with the root error thingy can someone elaborate on that.

 Did you resize the recovery partition? If not check the size of that partition, usually they are only a few GB in size as everything is compressed on them. You want to check the size to see if you have enough space to install Ubuntu on it.

Sorry I didn't read your last post. I see this is taken care of already.

---

