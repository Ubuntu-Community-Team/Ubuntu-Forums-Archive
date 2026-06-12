---
title: "[SOLVED] Fileserver with more than one hard drive"
date: 2008-07-26
forum: Networking &amp; Wireless
---

### Post by markdavidoff on 2008-07-26
I'm running a file server at home to share files across windows computers using ubuntu for servers and samba.
Recently I added a new hard drive to expand the amount of space available.

I have a directory called public (with the ability for all to read, but for the owner to write) with folders such as Music, Videos, etc. on my first hard drive.
I want to expand on my space with the second hard drive, but i want to keep my current setup and folder structure.

Is there a way for the server to use the other hard drive when space on the first hard drive is full while maintaining the same directory structure?

I know it's possible to mount the second hard drive in a sub-directory in the the public folder, but then I'll have an extra directory.
I also know I can move all videos, for instance, to the second hard drive and mount that in the public folder, but that's not what I want either.

It must be possible somehow. How to huge companies with hard drive racks manage to do it?

---

### Post by ChrisHannam on 2008-07-26
Short answer LVM - logical volumes. 

I personally built a RAID 0 setup [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid) With RAID 0 you can just add disks to increase size. But you have the risk of disk failure increasing every time a disk is added.

This might not be ideal as you might need to build an array which may mean you have to reformat your existing disk.

---

### Post by markdavidoff on 2008-07-27
The RAID page on the ubuntu wiki explains the RAID 1 setup (with mirrors) but not the one you speak of (RAID 0).

How do you set up RAID 0?

Do you need special hardware? My server computer is relatively old and uses IDE drives, not SATA.

---

### Post by david83 on 2008-12-30
Sorry to reply on an old topic, but for the far I know it is possible to create a RAID setup with IDE drives.

---

### Post by markdavidoff on 2008-12-31
LVM was the answer.

I formatted and reinstalled ubuntu on an LVM.

I also made another post (now solved) on mounting the LVM:
[http://ubuntuforums.org/showthread.php?t=887478](http://ubuntuforums.org/showthread.php?t=887478)

hope that helps anyone that is also struggling

---

