---
title: "Access issues to cpu harddrive via 9.10 Live CD"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by edxabbey on 2010-03-31
Hi friends,

I have been trying for 4 days via the forums and linuxquestions.org to fix this issue.  I am now pleading to the great Ubuntu Forums for help  

My problem:
-Tried to boot up OS, got the 'Busybox' issue that some have been having regarding boot delay.  This is the reason I decided I need to access my HD since this bug/problem does not have an easily searched solution in launchpad/forums/google, etc.

So, my solution, which I think may be easier, is to just access my harddrive, pull off my comics, ebooks, and some .avi files and just do a clean re-install.

I feel like I was making progress from using some mounting commands with my terminal, but I kept falling short.

For those who did not read all of that: I WOULD LIKE TO KNOW IF/HOW I MAY ACCESS MY INTERNAL HARDDRIVE WHILE USING A LIVE CD.

This community is the best.  I am a school teach and am on spring break, I will be hanging on your every post, so your help will not go unnoticed. 

Take Care,
ED

I have been in and out of my terminal, attempting to mount file extentions.  I have checked my fdisk read-outs

---

### Post by fromthehill on 2010-03-31
you should be able to see and access the partitions in the 'places' menu

---

### Post by edxabbey on 2010-03-31
The only thing I can access is the Filesystem that is loaded from the Live CD.  When I go to gparted I can clearly see that it is reading my internal harddrive, but I can not access it.  THIS SHOULD NOT BE CONFUSED WITH AN EXTERNAL DRIVE, I am trying to gain access to my cpu's HD only. (caps for clarification, not for increasing my volume.

Thanks for the reply.

---

### Post by edxabbey on 2010-03-31
I'm dying here friends.  Any help would be appreciated.

---

### Post by PRC09 on 2010-03-31
When you boot to your desktop from the live cd you should be able to go to  Places in the top menu bar and your internal drive should be listed.In mine it is listed as 76.9GB Media.You just have to double click and it will open and you can navigate to whatever file you want....If you dont see it in Places then you may have a problem with the drive itself or another hardware issue...Hope this helps.

---

### Post by spartan_87 on 2010-03-31
Have you tried mounting the partition manually? 

First make a mount directory
```
sudo mkdir /media/hd
```

Then mount the partition
```
sudo mount /dev/sda1 /media/hd
```

If it says "/dev/sda1 does not exist", try the command again but this time instead of sda1 try hda1.

---

### Post by edxabbey on 2010-03-31
This was the results of the first: 

```

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# sudo mkdir /media/hd
root@ubuntu:~# sudo mount /dev/sda1 /media/hd
mount: you must specify the filesystem type

```

When I adjusted to hda:

```

root@ubuntu:~# sudo mount /dev/hda1 /media/hd
mount: special device /dev/hda1 does not exist

```Thanks for the reply

---

### Post by LowSky on 2010-03-31
find the hard drive with
```
sudo fdisk -l
```

the mount using the command form before

```
sudo mkdir /media/hd_
sudo mount /dev/hda1 /media/hd_
```
the _ is the location of the hard drive you got from fdisk

---

### Post by edxabbey on 2010-03-31
I may have just looked more closely, or one of the many other mounts I tried, however, I can access my Home folder via the Media Folder now.


This may have helped:
```

root@ubuntu:~# mount -t ext3 /dev/sda1 /media/

```

---

