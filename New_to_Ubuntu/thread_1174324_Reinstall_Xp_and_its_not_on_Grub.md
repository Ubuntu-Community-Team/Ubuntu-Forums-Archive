---
title: "Reinstall Xp and its not on Grub"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2009-05-30
How do I come about figuring out which hard drive my xp install is on(like hd0,0 ect) so I can re add it to my grub

---

### Post by lindsay7 on 2009-05-30
First thing to do is type the following in the terminal

Sudo fdisk -l the letter l not the number 1

---

### Post by SpenceMakesSense on 2009-05-30
```
spence@spence-desktop:~$ sudo fdisk -l
[sudo] password for spence: 

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbcbcd60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37162   298503733+  83  Linux
/dev/sda2           37163       38448    10329795   83  Linux
/dev/sda3           38449       39019     4586557+  82  Linux swap / Solaris
/dev/sda4           39020       48641    77288715    7  HPFS/NTFS

Disk /dev/sdf: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         488     3919841    b  W95 FAT32

```

---

### Post by 73ckn797 on 2009-05-31
It looks like Windows will be on (hd3).

You may insert the following into grub at the very end:

```
#title        Microsoft Windows XP
#root        (hd0,3)
#chainloader    +1
```Reboot and see if it comes up on the grub boot menu.

I assume you know how to access grub to edit it?

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by SpenceMakesSense on 2009-05-31
ya I know how to edit it and stuff. Thanks!

---

### Post by 73ckn797 on 2009-05-31
> **SpenceMakesSense said:**
> ya I know how to edit it and stuff. Thanks!

That is why the assumption.

Hope it works out.

---

### Post by SpenceMakesSense on 2009-05-31
guess I spoke too soon. Not working actually says the selected disk does not exist

---

### Post by 73ckn797 on 2009-05-31
Is that via a grub error # being returned?

You may want to edit the line
```
root (hd0,3))
``` to read ```
rootnoverify (hd0,3)
``` .

---

### Post by SpenceMakesSense on 2009-05-31
hmm still no luck
Error number 21 if that helps

---

### Post by 73ckn797 on 2009-05-31
I know that Windows does "snot" like to be anything other than the first partition or hard drive. That may make things a little more difficult to deal with.

---

### Post by lindsay7 on 2009-05-31
I think there was an error with the drive and partition in the directions that you were given.  sda is drive hd0 and the windows partition is hd0,3 so instead of this

```
#title        Microsoft Windows XP
#root        (hd3,0)
#map        (hd3) (hd0)
#map        (hd0) (hd3)
#chainloader    +1
```

it should read root (hd0,3)

I do not think that you need the mapping lines since you only have one hard drive.  So If you edit the grub menu for windows it should look like this

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title           Microsoft Windows XP 
root            (hd0,3)
savedefault
makeactive
chainloader     +1
```



If you have a problem with getting Ubuntu to boot, do this.

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit

Tell us how you make out. You should be able to boot Ubuntu from the grub menu at startup and also boot windows xp at start up also. If you can boot Ubuntu but now windows after you do the above. You may need to redo you mbr. If you have your windows install disk handy we can fix that easily.


If you are still having trouble, post you grub menu here.

---

### Post by 73ckn797 on 2009-05-31
> **lindsay7 said:**
> I think there was an error with the drive and partition in the directions that you were given.  sda is drive hd0 and the windows partition is hd0,3 so instead of this

```
#title        Microsoft Windows XP
#root        (hd3,0)
#map        (hd3) (hd0)
#map        (hd0) (hd3)
#chainloader    +1
```it should read root (hd0,3)

I do not think that you need the mapping lines since you only have one hard drive.  So If you edit the grub menu for windows it should look like this

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title           Microsoft Windows XP 
root            (hd0,3)
savedefault
makeactive
chainloader     +1
```

If you have a problem with getting Ubuntu to boot, do this.

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hd0)
quit

Tell us how you make out. You should be able to boot Ubuntu from the grub menu at startup and also boot windows xp at start up also. If you can boot Ubuntu but now windows after you do the above. You may need to redo you mbr. If you have your windows install disk handy we can fix that easily.


If you are still having trouble, post you grub menu here.

OPPS!! I see what I did. It was late and now the error is obvious.

(hd0,3) is correct

---

### Post by lindsay7 on 2009-05-31
no prob, I get a little dyslexic on this all the time.

---

### Post by SpenceMakesSense on 2009-05-31
hey that worked thanks!

---

### Post by lindsay7 on 2009-05-31
Great!

---

