---
title: "Permissions in RAID"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by derek71 on 2010-04-29
I just reformatted my RAID 5 under ubuntu server 8.04 from ext3 to ntfs to experiment with file systems for a NAS I am putting to together.

I used: sudo mkntfs -v /dev/md0 to reformat the RAID.

Using the NTFS-3G driver, I added the following line to fstab: /dev/md0 /mnt/raid ntfs-3g auto defaults streams_interface=windows 0 0

The format process was successful, I have created a directory and set-up a share in Samba.

I wanted to change the owner/group for the share directory I created on the RAID and found that sudo chown would not change the directory.  No error messages are shown, so wonder if this is a problem with the RAID mount or the NTFS-3G driver?

---

