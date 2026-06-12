---
title: "I screwed up ftab"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by UncleRice on 2011-08-08
I changed fstab to mount my second drive automatically using my notes from several years ago, and now my 64 bit Ubuntu 11.04 is messing up at start up. I can start it in recovery mode, but I can't get fstab open so I can undo what I did. how do I fix this?

---

### Post by TeoBigusGeekus on 2011-08-08
While in recovery mode, can't you open fstab with
```
sudo nano /etc/fstab
```
?

---

### Post by UncleRice on 2011-08-08
Yeah! I had never heard of nano before. I have Ubuntu back. Now the following picture is how to break fstab:
[http://img847.imageshack.us/img847/3971/mounting.png](http://img847.imageshack.us/img847/3971/mounting.png)
How do I do it the right way?

---

### Post by whitesferry on 2011-08-08
i dunno but in your pic it says sbd1 .. should it be sdb1?

---

### Post by UncleRice on 2011-08-08
I did screw up the db thing. but now it complains about the unmask part.

---

### Post by garvinrick4 on 2011-08-08
Notice sda7 and sda8 one is ext4 format to automount and sda8 is NTFS to automount
Use its UUID to mount. Get the UUID using "sudo blkid" (lower case L without quotes)
The sda7 and sda8 are commented out so not in play just lets you know which is which.
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=e3d9f07a-86ae-4ef6-914e-a3ba9a879f82 /               ext4    errors=remount-ro 0       1
# /dev/sda7
UUID=0f7c5de9-c3b4-4c50-b288-d34e9ef6e119 /media/home      ext4   defaults    0
# /dev/sda8
UUID=1927A02F2C3A884A /media/data  ntfs-3g defaults,local=en_US.utf8 0 0


```
Here is link:[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by UncleRice on 2011-08-13
Ok, I think I'm closer, but something is still wrong.
[http://img52.imageshack.us/img52/3489/mount2.png](http://img52.imageshack.us/img52/3489/mount2.png)

---

### Post by coffeecat on 2011-08-13
You have both /dev/sdb1 and a UUID in the last line. You can have only one first field. Use one or the other.

By the way, please do not post images where you can post text which can then be edited and posted back by people helping you. For instance, for /etc/fstab, either highlight, copy and paste the contents of your gedit window into your post, or:

```
cat /etc/fstab
```

Highlight the output with the mouse, right-click and "copy" and then paste into your post. Enclose code such as this between [noparse]```
 and 
```[/noparse] tags otherwise you lose formatting.

---

### Post by UncleRice on 2011-08-13
Ok, finally got it to work like I wanted it to:
```
/dev/sdb1    /media/X    vfat    rw,user,auto,exec,umask=000    0    0
```
There may be extra option in there that don't need to be there, but both user accounts can now use my second drive like I want. Thanks for the up to date help.

---

