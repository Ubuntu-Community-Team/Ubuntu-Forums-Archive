---
title: "Dual boot problem"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Paul T. on 2010-05-01
Hi,

I've upgraded to Lucid and Ubuntu works fine overall, however I do have two boot issues, one minor prob with Ubuntu splash screens, but biggest issue is that I can't boot into XP, it is listed on the Grub menu, but if I select it I just get a blank screen with flashing white cursor in top left corner?

---

### Post by blazemore on 2010-05-01
Hello from Nottingham.

I'd recommend reinstalling grub.

On my machine, I have 1 hard drive called /dev/sda
It will probably be the same on yours but if you're unsure post the result of the command ```
sudo fdisk -l
```

Once you know the name of your drive, run the following commands to reinstall Grub, replacing the drive name if necessary:

```
sudo grub-install /dev/sda
sudo update-grub
```

PS. If you're in Nottingham and you're interested in Linux, why not come along to a Linux User Group meeting? There should be one very soon, subscribe to this mailing list for info: [http://mailman.lug.org.uk/mailman/listinfo/nottingham/](http://mailman.lug.org.uk/mailman/listinfo/nottingham/)

---

### Post by adm1968 on 2010-05-01
[FONT="Georgia"]Hi, Paul T
Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1466038](http://ubuntuforums.org/showthread.php?t=1466038)
[/FONT]

---

### Post by Paul T. on 2010-05-01
Hi,

sorry for delay in replying.
Tried advice in both above posts numerous times but no joy :(
Followed links to other methods including using chroot commands but zilch. When updating grub terminal reports no errors and lists both Linux & Windows, but Windows won't load :confused:

Here's result from fdisk -l command:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10d99b60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11151    89570376    7  HPFS/NTFS
/dev/sda2           11152       30401   154625625    f  W95 Ext'd (LBA)
/dev/sda5           11152       30136   152496981   83  Linux
/dev/sda6           30137       30401     2128581   82  Linux swap / Solaris

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4121584

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *

Am now going out for a drink, fed up of endlessly booting into and out of live cd to test system ](*,)


(Blazemore, thx for info about Nottingham Linux, am definitely interested.)

---

### Post by Paul T. on 2010-05-02
Beginning to wonder if problem is with Windows mbr and not grub?
here's output from grub update which seems ok, but windows will not boot:

paul@paul-desktop:~$ sudo update-grub
[sudo] password for paul: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done
paul@paul-desktop:~$ 


Unless anyone has any other ideas, will try repairing Windows mbr next, then restore grub from live cd :confused:

---

### Post by Paul T. on 2010-05-02
> **Paul T. said:**
> 
Unless anyone has any other ideas, will try repairing Windows mbr next, then restore grub from live cd :confused:

That did it! :P

---

