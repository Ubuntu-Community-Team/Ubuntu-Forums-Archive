---
title: "Permission denied on another Ubuntu setup"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by bugritall on 2009-08-05
I want to run programs that reside on another Ubuntu partition and I keep getting *Permission Denied* messages.

I think that I had better explain that I have cloned my Jaunty setup to another partition and then upgraded the clone to Karmic. I use Lazarus on Karmic to write/port software and these are the programs that I want to execute from Jaunty.

I have created appropriate entries in Jaunty's Applications Menu but they all return *Permission Denied* errors. Typically I'm trying to execute```
/mnt/test910/home/bugrit/lazarus/isa/isa
```from Jaunty, where *test910 *is my Karmic root partition and *isa* is the executable created by Lazarus.

I have examined all elements of the path and everything, including the target executable, permits "others" execution. I have also tried```
sudo /mnt/test910/home/bugrit/lazarus/isa/isa
```from a Jaunty command prompt but permission is *still* denied.

Help, please.

---

### Post by wojox on 2009-08-05
Here's the documentation on mounting:

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by bugritall on 2009-08-05
Thanks **wojox** but I'm not sure why you would direct me there. My 4 hard drives are all sata and are treated by Ubuntu as removable media. They mount like a cdrom does, in /media and on the desktop. This isn't what I wanted so I created some folders in /mnt and adjusted fstab:
```
LABEL=test910 /mnt/test910 ext4 auto,users,defaults 0 0
LABEL=XP /mnt/XP ntfs auto,users,defaults 0 0
LABEL=Music /mnt/Music ntfs auto,users,defaults 0 0
LABEL=Transit /mnt/Transit ntfs auto,users,defaults 0 0
```The partitions are now accessible *without* appearing as removable media on my desktop.

I can access all the ntfs partitions without difficulty and the problem arises only with test910, an ext4 partition.

Are there any clues in the foregoing as to what might be wrong?

---

### Post by spiderbatdad on 2009-08-05
please try sudo -i then run your mnt command

---

### Post by bugritall on 2009-08-05
Many thanks **spiderbatdad**, that did the trick and I can now run my Karmic-created apps from Jaunty.

I had to unmount and mount /dev/sda9 (Karmic) specifically for it to work. When I tried to unmount Karmic and use *mount -a* (to implement the mount via *fstab)* it didn't have any effect.

I have had a look at sudo's -i option and found it more than a little confusing but I note that it takes a step back with regard to initialising the environment. Whatever's going on there is beyond my ken at present but, for convenience, is there a way to do achieve the same result automatically during boot, say in fstab, please?

---

### Post by spiderbatdad on 2009-08-05
> **bugritall said:**
> Many thanks **spiderbatdad**, that did the trick and I can now run my Karmic-created apps from Jaunty.

I had to unmount and mount /dev/sda9 (Karmic) specifically for it to work. When I tried to unmount Karmic and use *mount -a* (to implement the mount via *fstab)* it didn't have any effect.

I have had a look at sudo's -i option and found it more than a little confusing but I note that it takes a step back with regard to initialising the environment. Whatever's going on there is beyond my ken at present but, for convenience, is there a way to do achieve the same result automatically during boot, say in fstab, please?

Am thinking to try in fstab by uuid. obtain uuid with devices connected
```
ls /dev/disk/by-uuid -alh
```Assuming you are familiar with this post, but in case you're not:[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by bugritall on 2009-08-05
**spiderbatdad**, I adjusted fstab to use my Karmic partition's UUID and booted the machine but it made no difference.

Thanks for the *How to fstab* link. I don't think I have seen that before or, if I have, I haven't studied it closely. The answer is probably in there but it's after 2am here in England, so it will have to wait until tomorrow. I'll keep you posted and thanks again for the help.

---

### Post by bugritall on 2009-08-05
I couldn't sleep. The problem was of my own making and the fstab entry for my Karmic partition now reads:
LABEL=test910 /mnt/test910 ext4 auto,users,defaults 0 0

I have reverted to using the label ID because I am an inveterate tweaker and it's easier to remember. :D

---

