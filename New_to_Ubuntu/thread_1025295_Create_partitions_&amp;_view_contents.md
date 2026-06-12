---
title: "Create partitions &amp; view contents"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by edzell on 2008-12-29
I keep abandoning then coming back to Ubuntu in the hope of getting an understanding of (among other things) where it puts everything. I have it installed dual-boot together with XP, and I THINK I created a separate partition for /home when I did it. Haven't been using it for quite a while and I forget what I actually did when installing.

Now I'm trying to check whether /home really is or is not in a separate partition but damned if I can find a way to view the partitions, other than boot up in Gparted but that doesn't let me see what directories they contain - ???

I now have a new(er) PC and a big(ger) HD and want to do a dual install on that, using a separate ntfs data partition so that both XP and Ubuntu can access compatible files. If I use Gparted to first create an ntfs partition and call it home, will /home automatically be located in that partition when I instal ubuntu? What other directories should I create separate partitions for, and how do I do it?

Sorry for the naivete of my questions - I WANT to embrace Ubuntu but this stuff is hard to find one's way around, without any relevant background.

Thanks, Edzell

---

### Post by lykwydchykyn on 2008-12-29
They key to what you need is the fstab file (/etc/fstab).  This is the file that connects partitions to mountpoints.  It is read by the kernel at boot, which then mounts each partition to the right mountpoint.  

Partition name (I assume you actually mean "label") means nothing, it's just a convenience (you can access partitions by label).  

Finally, using NTFS for /home is a bad idea. If you want a data partition to share with Windows, you're better of mounting it somewhere else.  Stick to ext3 or another "native" linux FS.  

You can see what is mounted at any time by typing "mount" into a terminal.  There's probably a GUI tool for that too, but I've never bothered to look for one.

---

### Post by hyper_ch on 2008-12-30
you can't use ntfs as /home.

---

### Post by jerome1232 on 2008-12-30
> **edzell said:**
> 
Now I'm trying to check whether /home really is or is not in a separate partition but damned if I can find a way to view the partitions, other than boot up in Gparted but that doesn't let me see what directories they contain - ???


A couple commands that will show you where things are currently mounted; either one works, 

```
mount
df
```

---

### Post by xjcannonx on 2008-12-30
although I will point out that it should very well be possible 
(for me I used my XP partition and that worked just fine while i had it) to create a separate NTFS partition and have it shared by both OS's

My /home didn't link to it directly but rather a symbolic link was created to link to that partition. You'll need ntfs-config from the repo's and that will provide read/write access and mount it automatically at start and then you just need to make a symlink with the ```
ln -s
``` command

I will say that a separate ext3 partition is the better way to go in my opinion though

---

