---
title: "How do I format my Windows partition and merge it with Ubuntu?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by h-town on 2009-05-16
Yes, after over a year of dual booting Ubuntu and Windows I've decided to use Ubuntu exclusively. But, what I need to know now is how to format my windows partition and merge it with my Ubuntu partition without loosing any data (such as documents or music, etc) that is already located on my Ubuntu drive.

I'm aware of Gparted but I need to know if I will be able to do what I wish before I start formating drives and merging them. :D

---

### Post by SunnyRabbiera on 2009-05-16
Well the problem is that if you intend on reformatting your partition it will loose data.
The only way to ensure nothing is lost is to back things up.
I personally say leave the windows partition alone for now until you can back it up.
External hard drives are real cheap these days.

---

### Post by h-town on 2009-05-16
I don't need to save anything from my windows drive. It's ready and waiting to sink into the void, forever.

I just don't want to lose anything from my Ubuntu drive. That does not need to be formated in any way whatsoever.

---

### Post by Locutus_of_Borg on 2009-05-16
```
sudo -i
for dev in `fdisk -l|grep FAT32|awk '{print ( $1 ) }'`;do umount $dev && mke2fs -j $dev && mkdir /storage && mount $dev /storage && echo "$dev /storage ext3 defaults 0 0" >> /etc/fstab && echo "what the hell did I just do?"; done

```
i was really considering trying to put in some resize2fs commands into that to expand your root file system into the empty space, but it was getting too complicated in my head, and without knowing your layout, too hard to write something to guess at it with any accuracy, so the above command should just format it to ext3 and mount it at /storage

---

### Post by SunnyRabbiera on 2009-05-16
Well you could use Grub to delete and reformat your windows partition and set the mount point of it to /home or something then.
But do you already have a separate home partition?

---

### Post by pastalavista on 2009-05-16
The easiest way to do it is with gparted. From the live CD. You can't do it within Ubuntu because you can't unmount the drive. Just delete the windows partition and leave it as empty space. Then resize-expand the / drive to fill the space. I've done it several times and never lost anything on the original Ubuntu install.

---

### Post by TheNosh on 2009-05-16
i'm pretty sure you don't lose anything in your ubuntu partition when you extend it into the space left by your windows partition. i've never done it myself though, cause i still use windows to play a couple of games i'm to lazy to get working in wine.

however you will obviously lose everything on the windows partition... thats kinda the idea

---

### Post by bumanie on 2009-05-16
You can use gparted to format the windows partition and then extend the ubuntu partition. You will find that your computer will not boot as grub will be pointing to the wrong partitions, therefore you will have to reinstall grub (from a live cd) to the mbr and have it recognize the new partition structure. 

After the re-partitioning. You will have to boot via a live cd and go to terminal to reinstall grub. I suggest you read [this]("http://users.bigpond.net.au/hermanzone/p15.htm") and ask any questions if things aren't clear. If there is only one hard drive with ubuntu you should be able to reinstall grub by > sudo grub > root (hd0,0) > setup (hd0)>  quitReboot and ubuntu should boot.
Also, be aware that if there is any sort of power disruption during partitioning, you will have to reinstall ubuntu as the filesystem will be wrecked, so it is best to back up first just in case there is a momentary blackout or power surge. If there is no interruption, gparted has always done a great job whenever I have partitioned.

---

### Post by h-town on 2009-05-16
I see, thanks for the help guys :)

---

### Post by Jazzy_Jeff on 2009-05-16
No matter what, you want to back up anything important. There are so many things that can happen to mess things up. It is always better to be safe than sorry.

---

