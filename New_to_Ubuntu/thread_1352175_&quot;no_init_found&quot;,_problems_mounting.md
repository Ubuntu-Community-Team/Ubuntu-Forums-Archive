---
title: "&quot;no init found&quot;, problems mounting"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by Planker on 2009-12-11
I an running Ubuntu 9.10 Netbook Remix on my Asus 1000 netbook. It had been running fine since the upgrade. However, recently I attempted to boot up my netbook only to be met with the error message:

Target file system doesn't have /sbin/init
no init found, Try passing init=bootarg

After some googling, I saw a post here:

[https://answers.launchpad.net/ubuntu...question/63005](https://answers.launchpad.net/ubuntu...question/63005)

where someone mentioned that, to solve the problem:

> 
Boot from the Live CD.

Run sudo fdisk -l The output will be will be a list of your partitions which you need to identify your root partition (usually this is sda1)

You need to mount that partition to access the files:
sudo mkdir /media/root
sudo mount /dev/sda1 /media/root

Browse to /media/root/boot/grub and look at menu.lst and make sure that references the correct sda# value.
Browse to /media/root/etc/ and look at fstab and see if the values are correct (you can also replace the uuid values with the sda# values in the comments),

If that doesnt work you need to run update-grub from inside your disk so with the drive mounted as above:
sudo chroot /media/root/
sudo update-grub


I am getting stuck at the step:

"sudo mount /dev/sda# /media/root"

My sda1 corresponds to the windows partition and the sda3 corresponds to the windows backup partition that came with my netbook. When I try to mount sda2 or sda4, I'm met with the error message:

mount: you must specify the filesystem type

I'm not sure how to specify the filesystem type. I'm still very much a newbie to ubuntu. I'm desperately trying to regain access to my files. Can anyone offer some advice? Thanks. I am DESPERATE!!

---

### Post by Planker on 2009-12-20
For anyone in a similar situation, I managed to fix things by following the advice [here]("http://www.reddit.com/r/Ubuntu/comments/ag5yj/ubuntu_910_refuses_to_boot_please_help/").

---

