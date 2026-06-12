---
title: "Can't boot. UseLiveCD to revert back to grub2"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-10-03
I first uninstalled grub2 and went to legacy grub becaue I found it easier to change the boot entries and take out memtest and stuff. Now, I can't boot and am forced to use the livecd. How can I revert back to grub2 using the livecd?

---

### Post by UnknownFear on 2010-10-03
I found where to revert back to grub2 using the livecd on the Ubuntu documentation.

Now, I need some help. I installed Mac first, than Windows, ending with Ubuntu. I am trying to execute the correct order of commands. Here is the output so far:

```

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8fc4cc65

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26        4889    39065368   af  HFS / HFS+
/dev/sda3   *        4889        5133     1952768   82  Linux swap / Solaris
/dev/sda4           14632       38914   195045376    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

Any ideas?

---

### Post by jrev on 2010-10-03
Check first the Ubuntu version you wantto install with the CD-live.
Then If you can connect to the Net with the live-CD, start the installation :)

---

### Post by UnknownFear on 2010-10-03
> **jrev said:**
> Check first the Ubuntu version you wantto install with the CD-live.
Then If you can connect to the Net with the live-CD, start the installation :)

You mean just reinstall Ubuntu? I guess I could do that. ^_^

---

### Post by jrev on 2010-10-03
I bet you can ! :)

---

### Post by UnknownFear on 2010-10-03
> **jrev said:**
> I bet you can ! :)

Yeah, it worked. I'm an idiot ^_^

---

### Post by jrev on 2010-10-03
Hope you enjoy it :)

---

### Post by UnknownFear on 2010-10-03
...I need some more help :( I went to edit the grub.cfg and change the titles and stuff, and it worked, but now Ubuntu isn't being displayed in GRUB. I am back in the livecd and I did make a copy of grub before I made changes so now I want to delete the current grub folder, make grub.old the "new" grub folder, and update grub to the original grub menu I had before I edited it. How do I do that?

---

### Post by cap10Ibraim on 2010-10-03
> **UnknownFear said:**
> ...I need some more help :( I went to edit the grub.cfg and change the titles and stuff, and it worked, but now Ubuntu isn't being displayed in GRUB. I am back in the livecd and I did make a copy of grub before I made changes so now I want to delete the current grub folder, make grub.old the "new" grub folder, and update grub to the original grub menu I had before I edited it. How do I do that?
.. so open the old grub.cfg copy its contents to the current file 
  ```
gedit  /etc/default/grub
```
then
```
update-grub 
```

---

### Post by drs305 on 2010-10-03
> **UnknownFear said:**
> ...I need some more help :( I went to edit the grub.cfg and change the titles and stuff, and it worked, but now Ubuntu isn't being displayed in GRUB. I am back in the livecd and I did make a copy of grub before I made changes so now I want to delete the current grub folder, make grub.old the "new" grub folder, and update grub to the original grub menu I had before I edited it. How do I do that?

Mount your real Ubuntu partition:
```
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda1 /mnt
```

Replace the file or open for editing:
```
sudo mv /mnt/boot/grub/ /mnt/boot/grub/grub.bad/
sudo mv /mnt/boot/grub.old/ /mnt/boot/grub/
```

You actually don't have to update grub in this case since when you boot the (old - original) grub files will be read. If you wanted to do it from the LiveCD, you would need to *chroot* into your Ubuntu partition. I have instructions in my signature line (you would not use the entire list of instructions) but it shouldn't be necessary.

---

