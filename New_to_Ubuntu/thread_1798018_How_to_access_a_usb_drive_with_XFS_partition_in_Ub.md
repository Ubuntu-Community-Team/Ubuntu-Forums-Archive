---
title: "How to access a usb drive with XFS partition in Ubuntu"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by martinkaz on 2011-07-05
I have a shitty LaCie Network Space 2 1TB , with my windows home network that suddenly stop working.
I open the cage (very easy, without breaking anythin), i ve connected the drive with a USB/SATA adapter, but it does not appear in my ubuntu installation.

please HELP!  I need to access this god damn drive

---

### Post by SeijiSensei on 2011-07-05
Did you try running xfs_repair against the filesystem?  If you don't have that program, you need to install the xfstools package.

My experiences with XFS on an external USB drive were horrible.  Any power outage cost me dozens of files.  I now use ext4 exclusively.

---

### Post by SeijiSensei on 2011-07-05
Did you try running xfs_repair against the filesystem?  If you don't have that program, you need to install the xfstools package.

My experiences with XFS on an external USB were horrible.  Any power outage cost me dozens of files.  I now use ext4 exclusively.

I'm assuming that Linux actually sees the drive, but can't mount it.  If it doesn't see the drive at all, your goose may be cooked.

---

