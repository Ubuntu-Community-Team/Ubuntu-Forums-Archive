---
title: "Grub problems"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by scorpious on 2011-06-11
I just upgraded to the latest version of ubuntu, everything seemed to work fine, I selected the option "keep existing grub" because that was the default option given. and after the restart I get
```
 
Loading operating system:
Boot from cd/dvd:
Error: symbol not found: 'grub_env_export'.
grub rescue>

```
Any help?
Cheers

---

### Post by FreymanX on 2011-06-11
Okay first off never go with Ubuntu 11.04...Its horrible...I've seen and used about 23 OS's and 11.04 is just not reliable at all. I would use 10.04, Its the best one from experience. So just install 10.04 and see if that changes.

---

### Post by wojox on 2011-06-11
You need to boot from a live-cd [and chroot]("http://ubuntuforums.org/showpost.php?p=10424577&postcount=8")

---

### Post by carvish on 2011-06-12
> **FreymanX said:**
> Okay first off never go with Ubuntu 11.04...Its horrible...I've seen and used about 23 OS's and 11.04 is just not reliable at all. I would use 10.04, Its the best one from experience. So just install 10.04 and see if that changes.
I so much agree with you, 11.04 is a nightmare right now. I tried to upgrade my laptop from 10.10 to 11.04, it didn't play nicely with Compiz, I lost my task bar, etc. . After a short while (4 hours)I reinstalled Meerkat, and my laptop has been purring like a kitten again. Maybe in a year or two they will work the bugs out. scorpious, I noticed you have 10.10 listed as your OS. I would stick with that or an earlier version for now. if you surf through these forums and you start seeing a lot less of the 11.04 listings then you can think about upgrading. Last year about this time Grub2 was all over the forum, now you don't see it very often. I use Grub2 as my bootloader and I am very pleased with it

---

### Post by jramshu on 2011-06-12
Going to have to boot a live cd and reinstall grub.

---

### Post by nzjethro on 2011-06-12
Yup, boot from a live CD, mount your partition where Ubuntu is installed (if you don't know, run sudo fdisk -l and look for the *).
To mount, run
```
sudo mount /dev/sd** /mnt
```
where the ** refers to the output of fdisk (mine is sda3, cos Ubuntu is on the third partition).
Then chroot (**ch**ange **root**) in, by running
```
sudo chroot/mnt
```
Run
```
update-grub
```
And then
```
grub-install /dev/sd**
```
(again, ** refers to the partition for fdisk).
Unmount with
```
sudo umount /mnt
```
Then reboot!

This page helped me a lot with chrooting and mounting when I forgot to run update-burg and cooked my boot:
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html) 
And yes, I agree with the above posters, run 11.04 from a live disk, but only upgrade if you are certain you will like it better than 10.10. I upgraded for a laugh a couple of weeks ago, gave it a few days, but I reinstalled Maverick because it's been rock solid for me.

---

### Post by wildmanne39 on 2011-06-12
> **scorpious said:**
> I just upgraded to the latest version of ubuntu, everything seemed to work fine, I selected the option "keep existing grub" because that was the default option given. and after the restart I get
```
 
Loading operating system:
Boot from cd/dvd:
Error: symbol not found: 'grub_env_export'.
grub rescue>

```
Any help?
CheersHi, make sure you use the livecd for 11.04 if you are keeping it, that was the problem when you chose to keep the old grub 11.04 using the newer grub and that caused it not to boot.

---

### Post by scorpious on 2011-06-14
I took the advice and went back to ubuntu 10.10. That solved the grub issue

Thanks

---

