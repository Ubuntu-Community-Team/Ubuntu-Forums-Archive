---
title: "Swap doubts"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by nishant.singh28 on 2010-02-01
I am not a complete newbie, but this is a totally unknown area to me. I have 4GB RAM on my system with Karmic 64 bit. RAM usage is almost never beyond 45%. It reaches 90% when I use Virtualbox(Win 7 32bit 2GB RAM VM). I have the following partition table:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              14        6173    49480200   83  Linux
/dev/sda3            6174       32269   209612800    7  HPFS/NTFS
/dev/sda4           32270       38913    53367930    5  Extended
/dev/sda5           32270       32518     2000061   82  Linux swap / Solaris
/dev/sda6           32519       33763    10000431   83  Linux
/dev/sda7           33764       38913    41367343+  83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x011a17b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2     7752256   244196032+   7  HPFS/NTFS
```The Swap area is 2GB(my bad). How do I expand it without a reinstall? I have almost 60gb free on sda3. Also, I don't want my system to use Swap area unless absolutely essential to get better speeds. How do I do that?
P.S.: The attached snapshot is just after I switched off Virtualbox.

---

### Post by s3a on 2010-02-01
Add "vm.swappiness = 0" without the quotes at the bottom of your /etc/sysctl.conf file which you can edit by issuing the following command:

```
sudo gedit /etc/sysctl.conf
```

and then reboot for the change to take effect. This takes care of making swap not be used for nothing.

As for resizing, on a live cd go to System-->Administration-->Gparted and right click on and shrink a certain partition and then grow your swap.

---

### Post by nishant.singh28 on 2010-02-01
OK. Right now, I'm on a live boot. The swap is in use even here, so i can't resize it.

---

### Post by chewearn on 2010-02-01
In gparted, right-click on the partition, select "swap off".

Or this command in terminal:
```
sudo swapoff -a
```

---

### Post by egalvan on 2010-02-01
Changing the swap partition (by growing or shrinking, etc) will 
change the UUID, which will cause problems with enumeration.

Copy down the UUID FIRST, BEFORE making any changes,
then restore it after the changes are made.

this will give you the UUID
```
sudo blkid 
```


I don't remember the code to set the UUID, but someone will come along soon... :)

---

### Post by nishant.singh28 on 2010-02-01
Why does resizing a partition take soooooooooooooo much time in Ubuntu. It took a hell lot less tome in Windows(sorry for the reference but i simply can't understand the reason). Just to shrink the 200 GB partition by 2 GB, it's taking 3 hours!!!!!

---

### Post by nishant.singh28 on 2010-02-01
OK I finally resized and booted and interestingly did NOT run into UUID problems. Either the system edited fstab accordingly by itself or the UUID didn't change to start with. Either way, thanks all :).

---

### Post by egalvan on 2010-02-02
It's possible that the UUID did not change.
It's not likely that the fstab was updated automatically,
but I have no experience with Karmic.

running

```
free -m
```

will tell the tale.


Here's what mine looks like:
```
ernest@gx:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2017       1709        308          0         13        922
-/+ buffers/cache:        773       1244
**Swap:         2831         [COLOR="Red"]39[/COLOR]       2792**
ernest@gx:~$ 

```

The value in red shows swap actually being used.
(yeah, i have a lot going on in this machine :) )

---

### Post by anaconda on 2010-02-02
a bit late, but you wouldn't have had to resize the swap. 
You could just have added a 2GB swap file on your home partition.

but whatever...

---

### Post by skymera on 2010-02-02
You can tune "swappiness" value to only use Swap if RAM is completey running out. This keeps as much in memory as possible.

3 years of using Ubuntu, never touched the swap.
Didn't have a swap partition for 2 years :P

---

### Post by nishant.singh28 on 2010-02-02
No problems folks. I don't have a problem with allotting a little swap. And I sometimes have to hibernate so I need swap.

---

