---
title: "I screwed GRUB up while upgrading to 10.04.  Help!"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by diablo75 on 2010-05-01
So while Ubuntu was upgrading it asked me to select the device that houses the Linux system and that if I wasn't sure about the drive to just select ALL devices to be on the safe side.  Well, I didn't do that, and selected what I thought would be the correct sda device.

Now when I go to boot, I get the following error message:

> GRUB loading.
error: the symbol 'grub_puts_' not found
grub rescue> (prompt with cursor)

I've got a Live CD up right now and am using it to post this message.

I've seen guides about how to restore Grub that are a little off for me because I have Windows XP installed on it's own partition (the partition I probably SHOULD have selected when asked where to put grub) as well as a / (root) partition and a /home/ partition (plus the swap).

Output of my fdisk -l looks like this:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9697acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749      121601   874361722+   5  Extended
/dev/sda5           21259      120951   800783991   83  Linux
/dev/sda6          120952      121601     5221093+  82  Linux swap / Solaris
/dev/sda7           12749       21258    68356512   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

Can someone help me with restoring grub2 on this system?

---

### Post by diablo75 on 2010-05-01
I got it fixed, using "Method 2" as shown here:

[https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

