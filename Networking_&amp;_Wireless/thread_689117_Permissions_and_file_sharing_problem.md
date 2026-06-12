---
title: "Permissions and file sharing problem"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by arddwyn on 2008-02-06
I am trying to share two partitions on my server using Samba and ssh. One of them (sdb1) is an NTFS formated partition and I am able to see the contents, add files and delte through ssh on Nautilus but when I try to access it through Samba I can see the partition but not the contents.

The second partition is (sdb4) Fat32 I can see the contents on shh on Nautilus but cannot make changes. For this partition I can't even see the contents in samba.
This are the permissions under /media

drwxr-xr-x 6 root root 8192 2008-02-06 00:20 music  (sdb4)
drwxrwxrwx 1 root root 4096 2007-03-10 21:35 store  (sdb1)

Ive tried to change the permissions on /media/music but they stay the same. Is there any way to make a  fat32 partition shared over a network?
thanks in advance to any one that can give me a clue

In case that it helps here is the smb.conf from the server computer:

[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passdb backend = tdbsam
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast lmhosts host wins
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[sdb1 public HD]
	comment = Public Photo folder
	path = media/store
	force user = nobody
	force group = no group
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes

[sdb4 Public HD]
	comment = Public folder
	path = /media/music
	force user = nobody
	force group = no group
	read only = No
	create mask = 0777
	directory mask = 0777
	guest ok = Yes

---

### Post by renzokuken on 2008-02-06
for sdb1, make sure the path is

```
/media/store
```

and not ```
media/store
```  (note the / you omitted)

restart samba and see if it helps

---

### Post by arddwyn on 2008-02-06
I added the / before media/store and reloaded samba on both computers but it was no go. Thanks though.

I saw on another that changing on fstab by adding unmask=0000 to the fat32 partition would allow to change  permissions, so I tried that and now I am able to read and write on both of them with ssh, but Samba still does not work for either one. :confused:

---

### Post by dgray_from_dc on 2008-02-06
Setting permissions on the mount point will not grant permissions on the file system.  You have to remember that FAT32 doesn't have the ability to distinguish file permissions and NTFS isn't native to Linux.  Most times when these file systems are mounted, they belong to root by default and are read-only to normal (and/or samba) users if they can be seen at all.

This was a problem I had until I decided to reformat my server disks ext3.

If this isn't an option (or is just inconvenient) you might try checking out and/or changing permissions in fstab.  If you mount the file system so that others can read and write to it, samba may not have problems.

---

### Post by arddwyn on 2008-02-06
Thanks, I changed the permisions on fstab and after rebooting: this are the permissions for the fat32 patition (/media/music)
drwxrwxrwx 2 root root 4096 2008-02-04 05:06 music

So it should be readable and writable but it still is not working on Samba.  Only on ssh.
The drive is empty so I could format it to ext3, I just wanted to try it this way in case that my partner wanted to stream music also to her Xbox. Otherwise all of our four computers run some flavor of Linux.

---

### Post by dgray_from_dc on 2008-02-06
Does the Xbox use UPnP?  If it does, look here [http://ubuntuforums.org/showthread.php?t=650020](http://ubuntuforums.org/showthread.php?t=650020)

It details how to set up MediaTomb to stream music and video to the PS3 but should work for all UPnP capable devices.

---

### Post by arddwyn on 2008-02-06
Cool. Thanks. Thats a monster that I am not touching yet. I want to get the server running and The Xbox will be if we can. For now accessing the drives with ssh through Nautilus should be enough

---

