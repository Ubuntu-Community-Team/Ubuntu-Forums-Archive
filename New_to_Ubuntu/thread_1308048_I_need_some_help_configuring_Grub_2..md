---
title: "I need some help configuring Grub 2."
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Muffinabus on 2009-10-31
I've tried figuring this out on my own but haven't successfully gotten it to work.

All I would like to do is add Windows 7 to the menu without modifying the Windows MBR whatsoever (does automatically adding it via sudo update-grub do this?).  It's on a separate hard drive.  fdisk:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33eb33ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       14594   117115904    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003fab9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29649   238155561   83  Linux
/dev/sdb2           29650       30401     6040440    5  Extended
/dev/sdb5           29650       30401     6040408+  82  Linux swap / Solaris
```


With Grub legacy I've always used 

```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

to add my Windows drive to the menu.  What is the Grub 2 equivalent?  How do I go about doing this?

---

### Post by ikisham on 2009-10-31
Grub(2) detects Windows' bootloader automatically. Sudo update-grub should do the trick.

---

### Post by Muffinabus on 2009-10-31
> **ikisham said:**
> Grub(2) detects Windows' bootloader automatically. Sudo update-grub should do the trick.

It doesn't modify it in any way?

---

### Post by ikisham on 2009-10-31
> **Muffinabus said:**
> It doesn't modify it in any way?

No. (like if you had Win7 and Vista bootin' through Vista bootloader, Grub would point to the - Vista - bootloader and then jump to the options for 7 and Vista).

---

### Post by Muffinabus on 2009-10-31
Took a leap of faith and just did sudo grub-update and it added Windows 7 without any problems with Windows or its MBR.

However, there is now a problem booting into Ubuntu.  It won't boot unless it detects my Windows 7 hard drive.  The loading screen hangs if I try to boot into Ubuntu when I have the power unplugged on my Windows drive.  How do I fix this now?

---

### Post by ikisham on 2009-10-31
Sorry, I (wrongly) assumed it wasn't an external hd. Now this will need some research (for me at least). There may be a way to tell Grub2 that it's a removable device.

---

### Post by Crandom on 2009-10-31
Try running
```
sudo update-grub
```
and rebooting. If that doesn't work, read up on grub2 at: 

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

If it is not automatically detected post any error messages here and you may need to add some custom entries. I believe you may want this:
```

menuentry "Microsoft Windows 7 (on /dev/sda1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set <YOUR_PARTITION_UUID_HERE>
	drivemap -s (hd1) ${root}
	chainloader +1
}

```
Note partitions [(hd<x>,<y>) <-- the y bit] start at **1** and not **0**.

Find your disk's UUID by typing in a terminal:
```
sudo blkid
```
and it will be the entry next to /dev/sda1. Save the file.

**Do not EVER edit /boot/grub/grub.cfg**

Remember to run
```
sudo update-grub
```
to apply the changes. Now restart and hope.

**EDIT:** If it still doesn't work try changing the "drivemap -s (hd0) ${root}" to "drivemap -s (hd0) (hd1)"

---

### Post by ikisham on 2009-10-31
Muffin, the thread where the knowledgeable grub2 guys answer is at [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ikisham on 2009-10-31
One thing that may help solve this issue is when the grub menu appears, select Ubuntu's entry, press 'e' to edit it (don't worry, it's not permanent), select the linux line and delete 'quiet splash' from the end then press ctrl+x to boot. Then you can see the exact error that's happening and post in the thread I linked above.
Grub2 is new for everyone.

---

