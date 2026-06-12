---
title: "Can see HDD using Live CD, but installation cannot find it"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2008-12-06
Hello again,

I decided to finally try to dual-boot Intrepid on my gaming PC.  In the past trying to get Linux on this thing has been a very painful experience.  

I booted from the Live CD, and so far so good.  Things seem to be going more smoothly than with Hardy.  It sees all of my drives without an issue.

However, when I choose "Install," and select Manual, my primary O/S drive (which has Windows XP Pro 64 on it, and a smaller partition I set aside for Linux) is not seen.  I can click out of the install and browse the device separately, but inside the installation wizard I get nothing.

Is there something I can do to address this?  The drive is as follows:

Western Digital WDC WD740ADFD-00

Thank you!

~Nix

---

### Post by lovelyvik293 on 2008-12-06
If it is possible then post the screen shot of the partition editor at installation time.
And post the output of sudo fdisk -l.

---

### Post by Nixie Pixel on 2008-12-06
sudo fdisk -l:

```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb978e9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5164    41479798+   7  HPFS/NTFS
/dev/sda2            5165        6380     9767520   83  Linux
/dev/sda3            6381        8066    13542795   83  Linux
/dev/sda4            8067        9039     7815622+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa73fa73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15298   122881153+   7  HPFS/NTFS
```

You can see the partitions that I made trying to get Hardy working, but the device isn't seen by intrepid, only my second hard drive.

---

### Post by ugm6hr on 2008-12-06
The reason is here: [http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode](http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode)

It is an unfortunate bug in Intrepid, which was not there previously.

You can try unmounting the drives first.

Or easier to use the "Install Ubuntu without trying it first" option (or whatever it's called).

---

### Post by louieb on 2008-12-06
Unusually when the installer fails to see a drive. Its for one of two reasons. 1st is a non-standard partition table. fdisk shows the partition table to be just fine. so thats not the problem.

the 2nd is these are sata drives and for some odd reason the installer does not see them. I've not seen that first hand but I I've heard that if you go into BIOS and set the drive to IDE compatible then the installer can see the drive.  

If you don't feel like going into your BIOS setup and changing the mode, you might try the alternate CD. Same steps and questions as the live CD installer.  The difference is the alternate uses the Debian text based installer. Its just as easy to use as the Ubiquity installer found on the live CD. Nice how to use it here:    [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

Good Luck.

Thanks **ugm6hr** for the link. :DNow I know there a 3rd reason.

---

### Post by Nixie Pixel on 2008-12-07
Well, I don't know what resolved the problem, but it is now resolved.  I simply rebooted several times without trying anything new, and the HDD was seen by the installer.

:confused:

Thank you again for your assistance.

---

