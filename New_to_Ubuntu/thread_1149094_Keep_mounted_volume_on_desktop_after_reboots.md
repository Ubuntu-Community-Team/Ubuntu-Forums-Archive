---
title: "Keep mounted volume on desktop after reboots?"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by virthen on 2009-05-04
I have a partition with a mount point of /media/disk (FAT32) that always disappears after my computer reboots.  If I go to Places > the partition, it puts it back on the desktop.  I'd like it to stay on the desktop without me having to open it from the menu every time.

Can someone help me with this?  Could there be something wrong with my partitions?

Thanks, from a new ubuntu user.

Oh and I'm on Hardy Heron if that makes any difference.

---

### Post by ii Candor ii on 2009-05-04
> **virthen said:**
> I have a partition with a mount point of /media/disk (FAT32) that always disappears after my computer reboots.  If I go to Places > the partition, it puts it back on the desktop.  I'd like it to stay on the desktop without me having to open it from the menu every time.

Can someone help me with this?  Could there be something wrong with my partitions?

Thanks, from a new ubuntu user.

Oh and I'm on Hardy Heron if that makes any difference.

Maybe you could set it up as a startup item? -- to mount that drive?

---

### Post by y_garti on 2009-05-04
you can put it in the user script so every time you logged in the computer will mount this file system
i suggest that you do

if [ ! "$(ls -A /mnt/your mount folder)" ]; then

    and over here you mount script
fi

so if its already mount it will not try to mount again

---

### Post by y_garti on 2009-05-04
and don't forget that you need sudo and edit the sudoers file so he wont nudge you with password

---

### Post by pastalavista on 2009-05-04
Install pysdm, a GUI storage device manager.. ```
sudo apt-get install pysdm
```
It will be added to your System > Administration menu

---

### Post by michy99 on 2009-05-04
You can put a line in /etc/fstab to mount it automatically on booting.

```
sudo mkdir /media/disk
gksudo gedit /etc/fstab
```

Add this line

```
 /dev/sda1 /media/disk vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

but change 'sda1' to whatever partition it is.

---

### Post by neopsalmist on 2009-05-04
I think you can add that media to /etc/fstab and it should be on the desktop each time you boot. Go into terminal and type:```
sudo nano /etc/fstab 
```
Scroll to the last line and type something like the following:
```
/path/to/files   /media/disk   vfat   defaults   0   0   
```
Hope this helps!

---

