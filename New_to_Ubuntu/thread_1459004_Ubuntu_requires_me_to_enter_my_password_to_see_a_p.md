---
title: "Ubuntu requires me to enter my password to see a partition of my hard drive"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by NPV1597 on 2010-04-20
Hi all,

I have a partition of my hard drive with all of my music, movies, pictures, documents, etc on it. I cannot access it without first entering a password. This is annoying because rhythmbox cannot access my music without entering the password. Is there a way to automatically grant access to the partition on boot... This partition also is used by my windows 7 ultimate 64 bit install I dont know if that matters.

---

### Post by bcbc on 2010-04-20
Add it to /etc/fstab and it will mount automatically. 

```

sudo mkdir /media/Windows7
sudo blkid
gksudo gedit /etc/fstab

```
Add this to the bottom of /etc/fstab replacing xxx with the UUID of the partition shown by the blkid command above:
```
UUID=xxx /media/Windows7 ntfs defaults 0 2
```

Mount immediately using the following:
```
sudo mount -a
```

Edit: I am assuming it's an ntfs partition but blkid will tell you the type as well. If you hibernate under windows you may have problems mounting it in Ubuntu.

---

### Post by NPV1597 on 2010-04-20
Awesome thank you!

---

### Post by bcbc on 2010-04-20
> **NPV1597 said:**
> Awesome thank you!

You're welcome. 

I should probably add a warning - I haven't done this myself, but if you hibernate under ubuntu and then boot windows you may have some problems. I've done the reverse and ubuntu refuses to mount the windows partition, but I don't know how windows handles this.

---

### Post by rsroxxx on 2010-04-30
> **NPV1597 said:**
> Awesome thank you!

Hey, have u tried Hibernating after using the above automount solution...?
Coz i want to do the same, but i'm afraid, i might screw things up..!

---

### Post by jaycee23 on 2010-04-30
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by doas777 on 2010-04-30
jsut a word of warning, it is a bit dangerous to use an NTFS partition in linux full time (it mounts on every boot) because linux can't really maintain the filesystem. your linux volumes will get checked periodically, but your ntfs ones have to be checked and corrected from within windows, so unless you boot into windows about half the time you boot up, filesystem corruption can really pile up. this is especially true if you encounter hard reboots due to power issues, or system lock ups. 

one solution to this is a NAS. if your files are on a file server, and you access them via network share, it matters little to either win or lin what the actual file system is.

---

### Post by bcbc on 2010-04-30
I've heard some people say linux can't handle ntfs, and others say that this is a myth. I don't think normal use of ntfs causes any problems under linux, however if you have a power failure, force reboot etc. then likely you will have to run chkdsk under windows to fix it.

In terms of hibernating, logically, if you have an open file on an ntfs system you are going to (at best) lose changes if you then go and mount it under a different os.

As I said, Linux knows when the volume has been hibernated on Windows and won't mount unless you force mount - I have no idea whether the reverse is true (doubt it), and don't feel like testing it either. So my comments were merely a general warning.

---

### Post by doas777 on 2010-04-30
> **bcbc said:**
> I've heard some people say linux can't handle ntfs, ...
yeah, that is a bit of an overstatement, you're right. I think ubuntu handles ntfs fine for surgical uses. its only when the volume is persistently mounted, and ubuntu is the most used os that it can cause corruption, just from the incidental stuff that happens all the time like brown/black outs.

---

### Post by bcbc on 2010-04-30
> **doas777 said:**
> yeah, that is a bit of an overstatement, you're right. I think ubuntu handles ntfs fine for surgical uses. its only when the volume is persistently mounted, and ubuntu is the most used os that it can cause corruption, just from the incidental stuff that happens all the time like brown/black outs.

I guess you have unstable power in your area? I can recall one time in the last 10 years that my computer has rebooted due to a brown out.

In any case, I have no specific knowledge that makes me qualified to say - yes ntfs is fine, or no it's not fine. I just think there are a lot of blanket statements about ntfs out there that seem over the top.

---

### Post by ndstate on 2010-04-30
What about if my NTFS file system is on a separate partition than the windows os?  IE:

Windows OS Partition -- Data Partition -- Ubuntu 10.04 Partition -- Swap Partition

Should I run into any corruption or hibernation problems?


...Not to hijack this or anything

---

