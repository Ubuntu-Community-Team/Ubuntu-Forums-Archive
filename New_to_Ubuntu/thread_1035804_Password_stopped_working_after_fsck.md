---
title: "Password stopped working after fsck"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by l1vewire on 2009-01-10
Hi guys,

Im relitavely new at linux but id love to learn. i had been running Ubuntu 8.10 on my Acer aspire one, but i have a huge problem.

My battery failed during a boot, so as i went to reboot the program ran the disk check, it came upon across an error and said fsck needed to run manually, which i did through the recovery after this my passwords (both user and root) do not work. 

i am at a loss and searching these forums i couldnt find anything relitave because i cannot get into a Root environment.

Can anyone help

Thanks
L1vewire

---

### Post by taurus on 2009-01-10
Boot with the LiveCD, open a terminal, and run

Applications -> Accessories -> Terminal
```
sudo fsck /dev/sda1
```
_Assuming_ /dev/sda1 is the partition you have to run fsck.

---

### Post by l1vewire on 2009-01-10
sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 1632 files, 1005536/1276665 clusters

fsck 1.41.3 (12-Oct-2008)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda2

fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3
Could this be a zero-length partition?


ubuntu@ubuntu:~$ sudo fsck /dev/sda4
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda5: clean, 150554/5373952 files, 2389748/10741452 blocks




I ran it for all the partitions i know. i believe 5 is my swap ans windows is my 1. im still at a loss because my ubuntu installation still tells me my password is wrong. help!

---

### Post by taurus on 2009-01-10
Please do not run fsck on windows partitions or you could trash them.

Did you install Ubuntu on /dev/sda4?

```
sudo fdisk -l
```

---

### Post by l1vewire on 2009-01-10
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        9148    68364607+   7  HPFS/NTFS
/dev/sda3            9149       14593    43736962+   5  Extended
/dev/sda5            9149       14497    42965811   83  Linux
/dev/sda6           14498       14593      771088+  82  Linux swap / Solaris


Id probably say its sda5 thats my linux

---

### Post by taurus on 2009-01-10
```
sudo fsck /dev/sda5
```
Once it's done, reboot and see if it boots normally.

And if you can't log in again, boot into recovery mode and change your password.

```
passwd mojo
shutdown -r now
```
Assuming mojo is your login name.

---

### Post by l1vewire on 2009-01-10
I ran sudo fsck /dev/sda/5, then rebooted.

i then loaded into recovery and Drop to Root shell prompt.

It says Give root password for maintinence
(or type Control-D to continue):

Nothing works. my old root passwd doesnt work it just says, login incorrect.

and Control-D just takes me back to the recovery Menu

---

### Post by taurus on 2009-01-10
Can you just boot with the normal kernel from GRUB menu?

---

### Post by l1vewire on 2009-01-10
yes it will boot to the logon screen but my password will not work

---

