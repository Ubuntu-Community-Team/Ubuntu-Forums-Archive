---
title: "Newbie looking to install dual boot with XP on pre partitioned HD"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by franasia on 2008-12-11
Hi everyone, I’m new to ubuntu and Linux.

I have searched the forum and could not find an answer to my need.

I want to dual boot install ubuntu 8.10 on my ThinkPad T42 running XP Pro SP3.

Hard drive is already partitioned into four partitions.  XP is on C: and one of the other three partitions is empty with a capacity of 20GB.

1.  Does ubuntu need to be installed on a partition next to XP (C) or can it be setup on any available partition?

2.  I tried installing from the Live CD but did not see an option to manually select to install on a specific partition on a pre partitioned HD.  Is this possible?

3.  If the above is possible, will the Partition Editor resize the selected partition creating the root, swap and home partitions?

Thanks for any help.

---

### Post by Exploited789 on 2008-12-11
just insert the live cd click install go through the setup and it will allow you to choose which partition you want to install ubuntu on, to my knowledge it doesnt have to be intstalled on "a partition next to xp" hope i helped

---

### Post by beno1990 on 2008-12-11
> **franasia said:**
> 
1.  Does ubuntu need to be installed on a partition next to XP (C) or can it be setup on any available partition?


Linux is designed to be capable of booting from any partition on the drive.

> 
2.  I tried installing from the Live CD but did not see an option to manually select to install on a specific partition on a pre partitioned HD.  Is this possible?


Yes, choose manual when it prompts you about the partition/drive setup you want and choose "/" as the mount point for the Linux install, and ext3 as the filesystem.

> 
3.  If the above is possible, will the Partition Editor resize the selected partition creating the root, swap and home partitions?


You'd have to delete the empty partition and create 3 new partitions in its place manually.

---

### Post by Duck2006 on 2008-12-11
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

If you have three partitions on your hard drive, and they are all primary partitions then you will have to make a logical partitions in side a extended partition and install ubuntu into there. There will be two partitions, one for /root, and one for swap.

---

### Post by Michael.Godawski on 2008-12-11
This guide can also be recommended:


[LIST]
[*][http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
[/LIST]

---

