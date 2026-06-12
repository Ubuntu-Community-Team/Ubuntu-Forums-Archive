---
title: "Upgrade to 11.04 runined my VM"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by abhishes on 2011-05-16
Had not booted my VM for a long time. Upon booting got prompted by the update manager to upgrade to 11.04

The upgrade ran for many hours... and everything was successful. 

I was prompted to restart the VM which I did. Now it does not boot up and this is the screen which I see

[IMG]http://farm6.static.flickr.com/5185/5729053658_a42628167d_b.jpg[/IMG]

---

### Post by wojox on 2011-05-16
This should get you loaded [Using CLI to Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

---

### Post by abhishes on 2011-05-17
Based on your suggestion I tried the following commands
grub>ls
(hd0) (hd0,5) (hd0,1) (fd,0)
grub>set prefix=(hd0,1)/boot/grub
grub>set root=(hd0,1)
grub>linux /vmlinuz root=/dev/sd01 ro
grub>initrd /initrd.img
grub>boot

It started to boot but got hung here

[IMG]http://farm6.static.flickr.com/5061/5729699340_3af1f76a6c_b.jpg[/IMG]

I also tried this

grub>set prefix(hd0,5)/boot/grub
grub>set root=(hd0,5)
grub>linux /vmlinuz root=/dev/sd05

But this failed here

[IMG]http://farm3.static.flickr.com/2224/5729161773_94cb45f857_b.jpg[/IMG]

---

### Post by abhishes on 2011-05-17
OK. I booted correctly. Here is what I did

grub>set prefix=(hd0,1)/boot/grub
grub>set root=(hd0,1)
grub>linux /vmlinuz root=/dev/sda1 ro
grub>initrd /initrd.img
grub>boot


Thanks a ton for your help

---

