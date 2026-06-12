---
title: "safest way to extend the size of home partition?"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by legolas_w on 2010-02-03
Hi
When I was installing linux I made a mistake and allocated an small partition (37GB) to /home and now it is getting full. The /home is located inside an extended partition but I have some unallocated space outside of that extended partition.

I am wondering whether it is possible to extend the /home size to outside of the extended partition into the unallocated space or not. if yes, can you please let me know how?

Thanks.

---

### Post by lovinglinux on 2010-02-03
I never tried (I use primary only), but I think it is possible. Although I never had problems, any partition reallocation involves risk, so backup your data.

You need to insert your Ubuntu CD and reboot from it. You might need to change the boot order to allow booting from the CD/DVD drive in the BIOS.

Then start ubuntu from the CD and got to "System >> Administration >> Partition Editor". You can do what you need from there. You will need to grow the extended partition to encompass the unallocated space and then grows the home partition (I guess).

[This](http://www.psychocats.net/ubuntu/separatehome) might help, although is intended for those who don't have a separate home yet.

You should also consider creating a new primary partition with the unallocated space and creating [symlinks](http://ubuntuforums.org/showthread.php?t=336591) inside home. For example, my home partition has only 9Gb and I use it only to store the configuration files. I'm currently using half of it. But I have two additional big partitions where I store all my personal documents, including lots of videos. These partitions have all those folders like Pictures, Videos, Documents, Music and so on . They are symlinked to home, so when I open the home directory with the file manager, they appear to be there, but they are physically stored on the other two partitions. This is really handy for situation like yours, because you can rearrange your data according to available space any time you want, as long as you create the proper symlinks pointing to the new locations.

---

### Post by semi_fiction on 2010-02-03
Yeah GParted is the way to go. I've used it many times without error.

---

