---
title: "Mounting partiton in the same place every time..."
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Blahah on 2009-01-19
Hi,

I have a partition (ext3) on which I keep all my media. Nautilus usually mounts this automatically as 'Removable Media' either on startup or when I open the link to the partition from the Gnome main menu.

The problem is, when the partition is mounted, it is not always to the same mount point. The auto-mount changes between the folder /media/Storage_ and /media/Storage-1 and seems to choose randomly between the two at startup.

I want the partition to mount reliably to the same mount point each time. I tried doing this with /etc/fstab and this worked, except that Nautilus still mounts the partition as well, meaning it is mounted twice. If I turn off auto-mounting in nautilus, I can no longer hot-plug a USB key.

Surely there is some way to ensure that my partition is always mounted to the same place, with only one mounting instace, whilst maintaining the hot-plugging feature?

Any help greatly appreciated.

-Blahah

---

### Post by mdewet on 2009-01-19
I had a mounting problem a while ago, not exactly the same as yours, but maybe this could be a staring point

[http://ubuntuforums.org/showthread.php?t=677711](http://ubuntuforums.org/showthread.php?t=677711)

---

### Post by mcduck on 2009-01-19
Easiest way to do this for removable drives is to set the label for your partition. (it's name).

The automounter will mount partitions using their labels as mount point instead of generic names if the partition in question has a label. (so if your partition's label is "blahah" the automounter will always mount it into /media/Blahah, and the icon on your desktop will be called "Blahah" as well.

How to set the label depends on what file system the partition has., for Et2/Ext3 partitions you can use the "e2label"-command:

sudo e2label *device* *newlabel*

---

### Post by hyper_ch on 2009-01-19
or if it's always connected add it to your fstab

---

### Post by Blahah on 2009-01-20
mcduck: the volume is already labelled, the problem was that with an fstab entry mounting to a folder with the same name as the label, I was getting a double mount of the same partition.

mdewet: thanks, I eventually solved all my problems by chowning the mount folder to root and setting default mount options in fstab, where before umask=000 was causing some error.

---

