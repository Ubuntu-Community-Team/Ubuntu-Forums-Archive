---
title: "Fix NTFS partition from Ubuntu"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by julian.irwin on 2010-09-21
I'm trying to reformat my friends hard drive using gparted from a live usb. When I look at the 'properties' menu for the disk that is to be formatted Ubuntu is telling me that I can't mess with the partition table until the drive is repaired by using chkdsk\f from the windows command line. The problem is that the reason I am formatting is because windows is broken and inaccessible. How can I run check disk (or a similar utility?).
Thanks!!:)

Julian

---

### Post by perspectoff on 2010-09-21
Use the Windows bootup disk in Repair mode.

---

### Post by Jerry N on 2010-09-21
Interesting - I ran into almost that same situation except that the problem was created by my earliest efforts at installing Ubuntu 10.04 along with EXT4.  Something about sector alignment or some such.  In one case, I was able to use Partition Magic or Parted Magic or Gparted Live (I don't remember which) and in the other case I had to boot a DOS disk containing FDISK.  For some reason, I have had better luck with one of the three listed partition management disks than I have with Gparted on an Ubuntu Live disk (I know - they all use Gparted).

Jerry

---

### Post by srs5694 on 2010-09-21
> **julian.irwin said:**
> I'm trying to reformat my friends hard drive using gparted from a live usb. When I look at the 'properties' menu for the disk that is to be formatted Ubuntu is telling me that I can't mess with the partition table until the drive is repaired by using chkdsk\f from the windows command line. The problem is that the reason I am formatting is because windows is broken and inaccessible. How can I run check disk (or a similar utility?).

Please be more precise. Do you mean you want to delete everything on the entire disk or just everything on one partition? If the former, you should be able to select Device -> Erase Partition Table in GParted to completely wipe the partition table and start over again. This will, however, leave *nothing* on the disk. If GParted refuses even to do that, "sudo dd if=/dev/zero of=/dev/sda bs=512 count=1" should do the trick.

If you want to erase just one partition, you should be able to do it from the command line even if GParted won't do it. Supposing the partition you want to erase is /dev/sda2, you'd type:

```
sudo mkfs.ntfs -f /dev/sda2
```

This will create a new filesystem (of type NTFS) on the partition. Be very careful about the partition specification (/dev/sda2 in this example). If you get it wrong, you'll wipe out some other innocent partition! If you want to install something other than Windows on the partition, you might do better to use another filesystem. Check the man page for the relevant utility (such as mkfs.ext3, mkfs.reiserfs, etc.) for the best options to use. (Usually none will work fine; I just included "-f" in my example because that will greatly speed up NTFS creation.)

---

