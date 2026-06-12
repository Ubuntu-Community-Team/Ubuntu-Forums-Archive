---
title: "Cannot access grub2 menu after installing Windows7 on seperate partition"
date: 2011-02-01
forum: New to Ubuntu
---

### Post by asuastrophysics on 2011-02-01
Hey guys,

I recently installed windows on a separate partition. In order to get the grub2 back, I've been following the "official" documentation on how to do so here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I followed all of the instructions to a T and I still can't access Grub2. 

Following the guide from "Overwriting the Master Boot Record" section:
I mount my linux partition with 
```
sudo mount /dev/sda1 /mnt
```
I then run ```
mount | tail -l
``` My Linux partition is listed as /dev/sda1 on /mnt type ext4 (rw)

I then ordered terminal to list the files in the /boot folder of the partition to verify that I had selected the correct one. All the files I should see in /boot are there.

I then installed grub as per the instructions. Now, I can only boot into grub shell. Any ideas on what I should do?

---

### Post by asuastrophysics on 2011-02-02
Fixed it by completely removing and then reinstalling grub2.

But doing that is easier said than done. You **_cannot_** simply run
```
sudo apt-get purge grub-pc
``` in terminal from the livecd. It won't work because you aren't executing the commands from your hard drive's filesystem. You must CHROOT into your partition and then run the commands. 

(If you want to know how to chroot into your partition, google it! That's how I found out how to do it.)

---

