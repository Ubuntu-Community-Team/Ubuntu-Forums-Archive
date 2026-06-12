---
title: "hard drive corrupt in windows not in ubuntu"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by sameer.india on 2009-08-08
I have a dual boot system vista/jaunty.
Also a seagate freeagentgo external harddisk (ntfs volume).
It works fine in jaunty but shows volume unreadable in vista.
chkdsk shows no bad sectors. I don't get the cause of this issue.
need some help.

---

### Post by Cato2 on 2009-08-08
.

---

### Post by Cato2 on 2009-08-08
If you can put this NTFS disk in another working Windows Vista PC and recover its disk there from Windows, that is by far the best option.

Ubuntu can't fix NTFS filesystems, but you could try this to extract your data, as long as you back up first.

1. Boot from an Ubuntu Live CD, this should auto mount your NTFS disks.  If it doesn't, try Gparted Magic, which definitely works with NTFS disks and has various recovery tools, and is generally focused on partitioning/recovering disks: [http://partedmagic.com/](http://partedmagic.com/)

2. Before you do anything else, back up the ENTIRE hard disk as a disk image to a spare hard disk - buy a new hard disk if necessary, you can always use it for disk to disk backups after you have recovered.  Read up on GNU ddrescue (gddrescue in Ubuntu repositories) and how to copy the whole disk, partition by partition - each partition should be a new file on your 'spare' hard disk, e.g. sda1.dat, sda2.dat, etc.  Use Gparted to see which partition has what, but don't mount anything until you have backed it up.

3. Try mounting the NTFS filesystem read-only and copy any important files off onto the spare disk - i.e. even if you can't recover your data from the disk, you still have the most important files.

4. Once you have recovered your data, reboot into Windows and re-format the filesystem.  Then recover your data onto the filesystem.

If you are new to Ubuntu this is quite a hairy procedure, but as long as you have a good backup first and take things slowly you should be OK.

---

### Post by mikewhatever on 2009-08-08
I don't think there is any need to 'recover the filesystem'. The disk is fine, the problem is with Vista.

---

### Post by Cato2 on 2009-08-09
This recent [Launchpad answer]("https://answers.launchpad.net/ubuntu/+question/78731") confirms that you can't fsck NTFS from Linux (i.e. filesystem check, like chkdsk in Windows).  The [ntfsck]("http://www.linux-ntfs.org/doku.php?id=ntfsck") tool is 'unavailable', though it does hint at using ntfsresize to check.

Bottom line remains that to check and repair the structure of an NTFS volume you should use Windows (and same version as wrote to the volume) - Linux is good for extracting data from a damaged NTFS filesystem, but it can't return the NTFS volume to a healthy state.

My original suggestions would also help check if there are really any bad sectors anywhere on the disk, by doing an image backup, and GNU ddrescue would extract the maximum possible data from the disk, setting any bad sectors to zero in the copied version.

---

### Post by sameer.india on 2009-08-11
there are no bad sectors.
windows disk manager shows it as RAW.
and windows scans it as an ntfs partition during startup.
And what do you mean by recover.
apparently the problem arises due to failure in unmounting the disk properly in ubuntu although i'm not sure.

---

### Post by Mark Phelps on 2009-08-12
According to what I read about the FreeAgent Go at the Seagate site, it comes with "encryption technology" -- implying that when you first set it up, you provide a password (or some other decryption key) to protect the data.  

It also mentions that it comes ready to do backups, implying that when you first connect it, you install some proprietary backup application.

Do you remember having to deal with either of these? (they may be optional, don't know -- don't have one of these).

---

### Post by sameer.india on 2009-08-13
encryption implys there is a folder where we can keep 'secret' data and that folder is encrypted
the backup application is for windows that comes in the drive and is actually optional

---

### Post by kansasnoob on 2009-08-13
Assuming your Windows is still operational it should be fully readable just by installing 'ntfsprogs' which is in Synaptic so it can be installed from there or terminal by:

```
sudo apt-get install ntfsprogs
```

It's also a very good tool to correct some NTFS problems, OTOH it's powerful enough to let someone destroy files necessary for Win to run:

[http://www.linux-ntfs.org/doku.php?id=ntfsprogs](http://www.linux-ntfs.org/doku.php?id=ntfsprogs)

---

