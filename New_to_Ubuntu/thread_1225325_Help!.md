---
title: "Help!"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Moe Z on 2009-07-28
Hi
   I don't know what've i done. After reinstalling windows, i lost my MBR.. so i tried to get it back. As a result...I can't boot any of my OS. It appears just black screen and..
grub>

pls help me.
here's my fdisk -l output

root@ubuntu:~# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe619e619

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3569    28667961    7  HPFS/NTFS
/dev/sda2            3570        9728    49472167+   f  W95 Ext'd (LBA)
/dev/sda3            4845        9728    39230698+   7  HPFS/NTFS
/dev/sda5            3570        3581       96327   83  Linux
/dev/sda6            3582        3830     2000061   82  Linux swap / Solaris
/dev/sda7            3831        4844     8144923+  83  Linux
root@ubuntu:~# 

PS: I'm now booting with Ubuntu 8.10 Live CD.
Someone help me pls :(

---

### Post by oldos2er on 2009-07-28
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Moe Z on 2009-07-28
when i tried
root@ubuntu:~# sudo grub-install --root-directory=/media/root/boot /dev/sda
The file /media/root/boot/boot/grub/stage1 not read correctly.

what's now ?? pls help me till end.. i'm helpless now :(

---

### Post by wojox on 2009-07-28
Not sure how yours is set up try:

```
root@ubuntu:~# sudo grub-install --root-directory=/media/root/boot /dev/sda5
```

---

### Post by Moe Z on 2009-07-28
root@ubuntu:~# sudo grub-install --root-directory=/media/root/boot /dev/sda1
The file /media/root/boot/boot/grub/stage1 not read correctly.

It still showing the same error..i've tried also the boot sectors i think.. like /dev/sda5 and /dev/sda7

root@ubuntu:~# sudo grub-install --root-directory=/media/root/boot /dev/sda7
The file /media/root/boot/boot/grub/stage1 not read correctly.
root@ubuntu:~# sudo grub-install --root-directory=/media/root/boot /dev/sda5
The file /media/root/boot/boot/grub/stage1 not read correctly.

---

### Post by julian.irwin on 2009-07-28
If nothing works you can just get another hard drive and copy all of your important files to from the old to the new using a live cd. It would suck but at least your not entirely screwed.

---

### Post by Moe Z on 2009-07-28
thx julian.. the problem is i've no extra hard drives :( but i think that's the last solution if any other solutions won't work..

---

### Post by Moe Z on 2009-07-28
Is there any other suggestions pls? i can't sleep if i don't fix this problem :(

---

### Post by cariboo on 2009-07-28
Use this [howto]("http://ubuntuforums.org/showthread.php?t=224351"), to repair grub. I used it several times and it works well.

---

### Post by Moe Z on 2009-07-28
I tried it.. but it still shows black screen although it works out every commands...:( my problem still don't fix yet and i'm still booting with the Live CD again..

---

