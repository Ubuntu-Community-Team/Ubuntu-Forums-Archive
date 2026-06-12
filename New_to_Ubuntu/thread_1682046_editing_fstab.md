---
title: "editing fstab"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Bentaylor on 2011-02-05
I'm an absolute beginner so please bear with me.

I've built a media PC running mythbuntu as the sole OS.  I built it with one hard drive but I'm trying to install a second.  So far, I've plugged it in, formatted as ext4 as a single partition.

I can mount the drive, explore it and add files, but I have to do this manually as when I restart the computer it is unmounted.  I've read that I need to edit fstab to get it to load manually, but I get a bit lost when trying to do this.  I've used a few text editors e.g. vi but I get a bit confused about what to do now.  I'm worried about accidentally messing things up if I do it wrong.  I can't seem to type text in through terminal anyway!

1) how do you edit the fstab file?
2) what would be the best place to mount the new drive?

Thanks in advance
Ben
[U][B]
My fstab file:[/B][/U]

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0
# / was on /dev/sda1 during installation
UUID=f62371fe-e796-4807-859b-1c84fa83e5b2  /            ext4  errors=remount-ro    0  1
# swap was on /dev/sda5 during installation
UUID=ab9a34fc-ad70-4129-be3c-a3e3026b4d21  none         swap  sw                   0  0
/dev/sdb5                                  /media/sdb5  swap  defaults             0  0

---

### Post by Morbius1 on 2011-02-05
This doesn't look right:
>  /dev/sdb5                                  /media/sdb5  swap  defaults             0  0     If you post the output of the following command we can see how your partitions are recognized by the OS:
```
sudo blkid -c /dev/null
```
And tell us what partition you want to mount.

---

### Post by Bentaylor on 2011-02-05
Thanks. I'll post that when I get back from work later!

---

### Post by ajgreeny on 2011-02-05
Try ```
gksudo gedit /etc/fstab
``` in terminal to give you editing rights to the file, then comment out (add # to start of line) the bottom line
```
/dev/sdb5                                  /media/sdb5  swap  defaults             0  0
``` so it looks like ```
# /dev/sdb5                                  /media/sdb5  swap  defaults             0  0
```save tyhe file and then ```
mount-a
```and report back here any errors.

Your problem is that you have two lines for swap on sda5, and I think that final one is incorrect.

---

### Post by Bentaylor on 2011-02-05
Morbius,

Blikid:
```
/dev/sda1: UUID="f62371fe-e796-4807-859b-1c84fa83e5b2" TYPE="ext4" 
/dev/sda5: UUID="ab9a34fc-ad70-4129-be3c-a3e3026b4d21" TYPE="swap" 
/dev/sdb1: UUID="9a3d74df-4621-4188-94e2-805bb29dfaf5" TYPE="ext4" 
```

I'm trying to mount /dev/sbd1

Ajgreeny,
That gedit tool seems to be just the ticket for editing the fstab file- I couldn't physically edit it before!!

I've done as you suggest and on running ```
mount -a
```, no messages appear

Thanks for your help so far!
Ben

---

### Post by ajgreeny on 2011-02-06
In that case everything is now OK, I think.  Run ```
free -m
``` in termional and come back with the output, just to check swap is on and how big it is.

---

### Post by Bentaylor on 2011-02-06
On Running free -m:

```
             total       used       free     shared    buffers     cached
Mem:          3852       3740        111          0         67       3143
-/+ buffers/cache:        529       3322
Swap:        11808          0      11808
```That gedit tool you showed me in the other thread was just what I was after and allows me to physically edit fstab.  I've added the following to the bottom:
```

UUID=9a3d74df-4621-4188-94e2-805bb29dfaf5 /var/lib/mythtv/hdd2 ext4 defaults 0 2
```which now seems to work well (slightly odd mountpoint as I'm going to be using it for media storage from mythtv, as per this thread  [http://ubuntuforums.org/showthread.php?t=1549200](http://ubuntuforums.org/showthread.php?t=1549200) )

So, thanks a lot for all the help- I now have a working hard drive, that mounts automatically on boot and works for storing media!!

---

### Post by ajgreeny on 2011-02-06
That's great!  An enormous swap partition, (11+ GB) presumably because mythbuntu runs better with a large swap?

---

