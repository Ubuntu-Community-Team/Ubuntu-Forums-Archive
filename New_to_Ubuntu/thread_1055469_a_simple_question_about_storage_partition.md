---
title: "a simple question about /storage partition"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by KevNice on 2009-01-30
Long story short: I had a storage partition, and a main Ubuntu partition (Hardy). I was messing with gparted and accidentally formatted the Ubuntu partition. I still have the storage partition.

I have since reinstalled Ubuntu (Ibex), and want to set it up again so that I can access the /storage partition from my Places menu. How do I do this? Also how do I edit the menu? There are some folders I want to delete because they are in the storage partition already (like music, videos, pictures)

Thanks

---

### Post by Gulyan on 2009-01-30
I think you must edit the /etc/fstab file,

Have a look [here]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by KevNice on 2009-01-30
hmm, my fstab file looks screwed up.

Here is the output of fdisk -lu:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      160649       80293+  de  Dell Utility
/dev/sda2   *      160650    93128804    46484077+   7  HPFS/NTFS
/dev/sda3        93128805   260654624    83762910   83  Linux
/dev/sda4       260654625   312576704    25961040    5  Extended
/dev/sda5       311034465   312576704      771120   dd  Unknown
/dev/sda6       260654751   305861534    22603392   83  Linux
/dev/sda7       305861598   311034464     2586433+  82  Linux swap / Solaris


```

The storage partition is /dev/sda3


but here is fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d3d36c65-8468-4a9a-84c0-1fc0a4da6aa4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=25a88678-da3d-435f-a92a-6bc49d93612d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by taurus on 2009-01-30
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda3   /media/storage   ext3   defaults   0   2
```
Save it and close down gedit editing window.  Now, create the new mount point and mount it.

```
sudo mkdir /media/storage
sudo mount -a
df -h
```
If you want to write to /media/storage without using sudo/gksudo, you can change the ownership of /media/storage from root to your login name.  Assuming your login name is kevin, you can do something like

```
sudo chown -R kevin:kevin /media/storage
ls -la /media
```

---

### Post by KevNice on 2009-01-31
Thanks a lot friend, that did the trick ;-)

---

### Post by KevNice on 2009-01-31
Sorry just one more question..

I have the storage partition in nautilus now, but it also appears mounted on the desktop. Is there a way I can remove it from the desktop while keeping it mounted and still able to get to it through the nautilus menu? I'm kind of a desktop clutter freak.

---

### Post by ibuclaw on 2009-02-01
Press **Alt+F2** and type in
```
gconf-editor
```
and press Enter.
Navigate your way through "**apps->nautilus->desktop** and uncheck the "**volumes_visible**" checkbox.


Or you could get [ubuntu-tweak]("http://ubuntu-tweak.com/2008/12/15/ubuntu-tweak-044-released.html"). Install it, go to "**Applications->System Tools->Ubuntu-Tweak**" and when the application starts, click "**Desktop**" and you'll see a check box titled "**Show mounted volumes on Desktop**" under Desktop Icons Settings. Clear it, and quit.

Regards
Iain

---

