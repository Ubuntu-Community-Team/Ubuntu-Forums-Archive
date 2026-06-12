---
title: "problem with partitions"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by Sejanus on 2009-12-11
I have dual boot ubuntu/vista. Using GParted live CD, I did the following:

1. Deleted Vista Partition. Then used new free space for:
2. Created new, much smaller partition for a new Vista install
3. Expanded Ubuntu partition.

After I boot Ubuntu again, I can see that Filesystem now has 90+ GB instead of former ~40, e.g. expanding seems to work. However, it reads that 90+% of it is used and there's only ~7GB free. Now thats a clearly newbish question but can it be that the old files from former vista partition make that much space used? I was expecting them to get deleted automatically the moment I deleted partition. In any case, how could I fix this? I want that space free ;) Thanks in advance

---

### Post by gordintoronto on 2009-12-11
No, it's not the old files.

Use Accessories/disk usage analyzer.

---

### Post by kansasnoob on 2009-12-11
It might be helpful to see the output of:

```
sudo fdisk -l
```

BTW that's a lower case L. It sounds like you have only one hard drive, if so the first line of that should show something like:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes


If it is sda (substitute proper disk ID otherwise) run:

```
sudo parted /dev/sda print
```

It's just a much more "human readable" list of partitions.

It would also be good to see the output of:

```
df -H
```

---

### Post by Sejanus on 2009-12-12
Mmm ok but now after I installed windows 7 in the new partition, linux does not load at all. I tried to fix it by moving boot flag in GParted Live CD, when I flag windows partition - windows loads, when I flag Linux partition - nothing loads ("Operating System is not found" message). Does it mean partition is somehow broken or just something wrong with loader? 
I really feel lame messing everything like this but oh well, practice helps to learn... :))

p.s. at good old times when everything worked, my *windows* partition was flagged as bootable, not linux. Nevertheless GRUB screen loaded everytime I booted PC so I could choose between Linux and Vista.

p.p.s. if you need any screenshots or additional info I can load Windows 7 with no problems, as well as GParted Live CD. Ubuntu nowhere to be found atm :|

---

### Post by Bartender on 2009-12-12
> **Sejanus said:**
> Mmm ok but now after I installed windows 7 in the new partition, linux does not load at all. 

If Linux was on the PC before you installed 7 then part of the Linux bootloader was removed.

---

### Post by Sejanus on 2009-12-12
> 
If Linux was on the PC before you installed 7 then part of the Linux bootloader was removed.
Right. How could I get it back?

And is it normal, or I should have done it in some other way to prevent removal? I just shoved in Windows CD, booted from it and installed in the right partition...

edit: nvm, with some intense googling I managed to get Linux back working. Now I will get back windows to GRUB menu and thats it. After all the messing with partitions the original problem with not-enough-space somehow disappeared, now I see correct free space size. Thanks again everybody :)

---

