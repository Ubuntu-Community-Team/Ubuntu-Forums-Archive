---
title: "Ubuntu Live CD/Gparted do not see existing NTFS &amp; ext3/4 partitions on HD"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by diablo75 on 2011-05-01
I have a home built system that I've been running Ubuntu and Windows on in a dual boot configuration for several years now, setup such that there were 4 partitions on the drive:

1 - Windows
2 - Ubuntu /
3 - Ubuntu /home
4 - swap

The upgrade failed.  When I tried to boot Ubuntu after the upgrade "successfully completed" it will hang during the Ubuntu splash screen and never move forward.

Running into crap like this is pretty typical for me during upgrades and I partitioned the hard drive as listed above for the sole purpose of being able to simply format the / partition, keep /home, and start with a fresh install.  The problem now is that Ubuntu (and a separate Gparted Live CD) do not see any partitions on the hard drive.  I am writing this post from Windows on the computer in question and it has no problem booting from the newly installed GRUB menu that came with 11.04, and yet both of these Live CDs seem to thikg the hard drive is empty and has nothing on it.  I can't tell it to format the / partition, and am quite sure that if I proceed with the re-installation it will format Windows as if it were never there and I will lose lots of valuable data.

Anybody have a clue as to why Linux is failing to read this hard drive properly yet the system is able to boot into Windows (and at least attempt to boot into Ubuntu) yet the partitions are not being seen.  Oddly enough, the Local Disk Storage Manager applet inside Windows XP's Administrative Tools>Computer Management panel is able to see all the partitions.

---

### Post by oldfred on 2011-05-01
Note Known Issues section
[https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes](https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes)

Usually partitions not seen in gparted is either a partition table issue or an error in a partition. My XP would boot, but gparted would not see entire drive. After running chkdsk it was fine. You may want to run e2fsck on the Linux partition.

Post this, may show partition issues:
sudo parted /dev/sda unit s print

More info on these links:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Missing Partitions in GParted - repairs info:
Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sda
Run chkdsk on any NTFS partitions even if they currently work.
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

If partition table issue back up table immediately:
Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by srs5694 on 2011-05-01
This symptom is usually caused by one of a handful of partition table problems, as described [here.](http://www.rodsbooks.com/missing-parts/index.html) The easiest solution is generally to run [FixParts](http://www.rodsbooks.com/fixparts/) on the disk. That said, if you want a more specific diagnosis, you should run the [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) on the computer and post the RESULTS.TXT file it produces here (between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility, please).

---

### Post by diablo75 on 2011-05-02
SOLVED!

Except I didn't use the provided solutions.  I was still able to access the grub menu on the HD when booting and decided to drop into recovery mode.  From there I just selected "Reboot into fsck" and it restarted the computer, I let it boot the normal mode Linux kernel at the top, and fsck started a check on all Linux related partitions.  It didn't tell me if it had fixed anything along the way, but it must have because I'm typing this post from Ubuntu with Unity looking beautiful.

Thanks for the help anyway!  I'm off to check out this new Unity business and see what else it does.

---

### Post by madjr on 2011-05-02
> **diablo75 said:**
> SOLVED!

Except I didn't use the provided solutions.  I was still able to access the grub menu on the HD when booting and decided to drop into recovery mode.  From there I just selected "Reboot into fsck" and it restarted the computer, I let it boot the normal mode Linux kernel at the top, and fsck started a check on all Linux related partitions.  It didn't tell me if it had fixed anything along the way, but it must have because I'm typing this post from Ubuntu with Unity looking beautiful.

Thanks for the help anyway!  I'm off to check out this new Unity business and see what else it does.

good to see ubuntu finally doing its job.

would be nice if these diagnostics executed automatically after bad upgrades and stuff.

---

### Post by diablo75 on 2011-05-02
> **madjr said:**
> good to see ubuntu finally doing its job.

would be nice if these diagnostics executed automatically after bad upgrades and stuff.

It might even be worth while to enforce fsck to take place right before an upgrade.

---

