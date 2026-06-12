---
title: "permissions for HDD"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Kenzo on 2009-06-02
I'm a novice at Ubuntu. I checked the posts and have tried several 'solutions' but can't get write access to an internal HDD. Have tried sudo chown -R user:user /media/sdb1 but get 'Operation not permitted'.

I want to be able to FTP upload to the HDD that is /media/sdb1.  It's formatted as fat32 owned by root. Can't seem to change the permissions.  I've read and tried a lot of the 'solutions' but not getting anywhere.  Tried to mod the group but no luck either.

Can't figure out what I am doing wrong.  Even tried to do it through Nautilus but doesn't work. Gotta be something simple that I'm missing....

How do I allow users other than root to RWX to the drive?

---

### Post by pastalavista on 2009-06-02
I have always done it with 'gksu nautilus' in terminal or alt-f2. Navigate to the filesystem /media, right-click sdb1 > properties > permissions.

---

### Post by taurus on 2009-06-02
How did you mount that drive, /dev/sdb1?  Did you have an entry in /etc/fstab to mount it?  You can set the ownership and permissions in /etc/fstab since vfat/ntfs filesystem doesn't work too well with chmod/chown command.

---

### Post by Kenzo on 2009-06-02
Thanks for the replies. 

Pastalavista - I tried to do it through Nautilus before I posted;)  I can't change the 'Group' nor 'Other' permissions. Trying to change the Group gives a message saying don't have permissions necessary (opened Nautilus with gksu). When I try to change the permissions for 'Other' they just revert to what they were.

Taurus - The drive is mounted in /media/sdb1 and yes there is an entry in /etc/fstab. <dump> is vfat. 

You are right about chmod and chown not working too well - tried that too:( 
What entries do I make to /etc/fstab?

---

### Post by Kenzo on 2009-06-03
I did chmod on /dev/sdb1 and ls -l shows the permissions that I set. However, the drive is in /media/sdb1. chmod doesn't seem to work for that.  When I do ls -l on /media/sdb1 the response is 'total 0'.

What am I doing wrong?  How can I set permissions for others to create files on the drive?

---

### Post by mcduck on 2009-06-03
> **Kenzo said:**
> I did chmod on /dev/sdb1 and ls -l shows the permissions that I set. However, the drive is in /media/sdb1. chmod doesn't seem to work for that.  When I do ls -l on /media/sdb1 the response is 'total 0'.

What am I doing wrong?  How can I set permissions for others to create files on the drive?

You can't change ownerships or permissions on FAT or NTFS partitions, as those file systems don't have any support for such features. (They are Microsoft's proprietary file systems, not made to support any advanced features used in Unix/Linux systems)

All permissions for these file systems are configured for the whole partition, at the time it's mounted. So, to get read/write permissions on those partitions you need to configure them in /etc/fstab to make the system mount the partition with suitable permissions.

This page should be helpful: [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Kenzo on 2009-06-03
Thanks McDuck. Much appreciated.  dmask and fmask have done the trick.:D

---

