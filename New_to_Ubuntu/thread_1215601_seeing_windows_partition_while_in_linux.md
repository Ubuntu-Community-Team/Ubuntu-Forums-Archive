---
title: "seeing windows partition while in linux"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by raysa on 2009-07-17
What determines whether you can see different media, and how do you change it?

I have my computer dual-boot with xubuntu 9.04 and windows xp (I stay in xubuntu most of the time and just fire up xp when I need to run a couple of specialist packages there). 

I used to be able to see the windows partition while in ubuntu - which was very useful for pulling over documents, images, etc.  But now it doesn't show up - no sign of it in the 'media' folder or where it used to be on the initial desktop.

I never could see the ubuntu partition from xp, but that would be very handy too.  Possible?

Thanks, Ray

---

### Post by Sidewinder1 on 2009-07-17
Perhaps you need to mount, manually the NTFS partition.
Go to Places---->Home Folder and you should see it listed in the left column; simply click it and it should mount. 
There is a windows driver you need to install within windoze (I forget the name of it, sorry, but do a search) so that win will "see" your linux partitions.

HTH,
Side

---

### Post by ~sHyLoCk~ on 2009-07-17
explore2fs can let you have read-only rights only!

---

### Post by Sidewinder1 on 2009-07-17
On a side note; I have 4 external hard drives, plugged into two different controller cards. One card auto-mounts as soon as I turn on the drive, the other card I have to mount the drives manually using the method above.

---

### Post by powel212 on 2009-07-17
you can use add/remove to install NTFS config. Once installed launch and and configure. 

The next time you boot your windows partitions will appear on your desktop.

Have fun

Powel

---

### Post by prshah on 2009-07-17
> **raysa said:**
> 
I used to be able to see the windows partition while in ubuntu - which was very useful for pulling over documents, images, etc.  But now it doesn't show up - no sign of it in the 'media' folder or where it used to be on the initial desktop.

I never could see the ubuntu partition from xp, but that would be very handy too.  Possible?



If you cannot see the Windows partition now, when you could before, then it is very likely "dirty", ie, not cleanly unmounted (maybe an interrupted Windows shutdown?). 

The simplest thing to do is to restart in Windows and shutdown cleanly; alternately, if you don't want to leave linux, mount it manually (at your own [negligible] risk)```
sudo mount -t ntfs /dev/sda1 /media/disk -o defaults,rw,force
``` Replace names as suitable to your system. Henceforth it will mount automatically, if cleanly unmounted.

To access your linux partitions in Windows, use Ext2 IFS from [www.fsdrivers.org;](www.fsdrivers.org;) While read/write access is available I recommend you use readonly access to prevent accidental deletions.

---

### Post by raysa on 2009-07-17
Thanks folks, but I'm still having trouble.
The partition doesn't show up in Places>Home so I can't mount it from there.

And now my 'add/remove' has disappeared from the Applications menu! It used to be right at the top but it has been replaced by a "Run program" tag. What's going on?

---

### Post by iamkrazee on 2009-07-17
Please do this:
```
sudo su
```
This will take you to root shell.


```
echo /dev/sda1 /mnt/drv1 ntfs-3g defaults,force,gid=users\n >> /etc/fstab
```
This will add the entry to your fstab so on every reboot it'll just work.

Then you can use your nautilus to add shortcuts to your desktop.

*TIP : Replace "sda1" with the appropriate name, using fdisk -l
Also, drv1 needs to be created in /mnt before using this. Use mkdir /mnt/drv1, /mnt/drv2 etc.

---

### Post by raysa on 2009-07-17
Thanks folks, but I have very carefully followed all these suggestions and none of them has worked.

A new piece of information: For reasons of incompetence I also have a partition on this computer with ubunto 8.10(Hardy) on it, which I meant to replace when I installed xubuntu 9.04(Jaunty).

If I fire up the old Hardy the Windows partition is visible and fully accessible, yet in Jaunty there's no sign of it.

Any ideas?  Thanks, Ray.

---

