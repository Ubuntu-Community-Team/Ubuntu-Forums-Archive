---
title: "Problems with Windoze shares"
date: 2005-09-18
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2005-09-18
I'd appreciate some help with how to identify and fully use certain 'doze shares.  Here's the setup in question:

PC #1: Dual-boot Ubuntu/XP
   Partition 1: recovery files for HP computer (FAT32); "drive d:"
   Partition 2: XP (NTFS); "drive c:"
   Partition 3: Ubuntu (Extended)
   Partition 5: Ubuntu (Linux)

PC #2: Windows '98 (entire hard drive; FAT32)

The NICs in PCs 1 and 2 are connected via crossover cable.

After adding the following line to /etc/fstab, all Ubuntu users (on PC #1) can see and read the files on the XP partition of the local hard drive:

/dev/hda2       /mnt/xp         ntfs    nls=utf8,umask=0222 0       0

However, NO ONE (including root) can write to it.

After using 'connect to server' all users can see and read the files on PC #2; again, though, NO ONE can write to it.

Now, my questions:

1) How do I make both drives writeable by all?

2) How do I make PC #2 available, for example, when using an application that lets you 'browse' for the location of a file to use.
2a) I suspect that this isn't done via the 'connect to server' method, but I can't figure out how to 'mount' it instead.

Thanks in advance for any help/advice!

---

### Post by cwaldbieser on 2005-09-18
[QUOTE=Old *ix Geek]I'd appreciate some help with how to identify and fully use certain 'doze shares.  Here's the setup in question:

PC #1: Dual-boot Ubuntu/XP
   Partition 1: recovery files for HP computer (FAT32); "drive d:"
   Partition 2: XP (NTFS); "drive c:"
   Partition 3: Ubuntu (Extended)
   Partition 5: Ubuntu (Linux)

PC #2: Windows '98 (entire hard drive; FAT32)

The NICs in PCs 1 and 2 are connected via crossover cable.

After adding the following line to /etc/fstab, all Ubuntu users (on PC #1) can see and read the files on the XP partition of the local hard drive:

/dev/hda2       /mnt/xp         ntfs    nls=utf8,umask=0222 0       0

However, NO ONE (including root) can write to it.

After using 'connect to server' all users can see and read the files on PC #2; again, though, NO ONE can write to it.

Now, my questions:

1) How do I make both drives writeable by all?

2) How do I make PC #2 available, for example, when using an application that lets you 'browse' for the location of a file to use.
2a) I suspect that this isn't done via the 'connect to server' method, but I can't figure out how to 'mount' it instead.

Thanks in advance for any help/advice![/QUOTE]

There is no reliable support for writing to NTFS partitions at this time (because the filesystem is closed).  Some experimental support is in the works, but most folks don't care to accidently destroy their NTFS filesystem.

The current state-of-the-art suggests that you can use samba for remote NTFS shares (because the Windows computer actually takes care of the actual writing to filesystem), or you need to have a FAT32 partition (for reading a local drive-- typical in dual boot scenarios).

The starter guide explains how to do this in the Windows section: [http://www.ubuntuguide.org/#mountunmountnetworkfoldersall](http://www.ubuntuguide.org/#mountunmountnetworkfoldersall) 

As far as browsing to a remote location, I think you can just use an smb:// URL instead of a normal file path.

---

### Post by Old *ix Geek on 2005-09-24
> As far as browsing to a remote location, I think you can just use an smb:// URL instead of a normal file path.For some reason, this just isn't happening for me.  For example, if I'm using gedit and want to 'open' a file that's on the remote Win98 PC, there's no way to access it.  It doesn't appear in the list of locations available to me, and there's nowhere to manually enter a different location.

---

### Post by Orborde on 2005-09-25
[QUOTE=Old *ix Geek]For some reason, this just isn't happening for me.  For example, if I'm using gedit and want to 'open' a file that's on the remote Win98 PC, there's no way to access it.  It doesn't appear in the list of locations available to me, and there's nowhere to manually enter a different location.[/QUOTE]
Share the file/directory on the Win98 PC (which I assume you did), make sure you have the smbfs package, and do this ```
mount -t smb '\\server_by_IP_or_hostname\sharename' /mount_point/
```
That worked for me in accessing my personal Windows share at my school. You may need to add -o username=blah to the end of that if it's set up to require a username. Otherwise, I *think* it tries to log you in with your username on the Linux system you're logging in from.

---

### Post by cwaldbieser on 2005-09-25
[QUOTE=Old *ix Geek]For some reason, this just isn't happening for me.  For example, if I'm using gedit and want to 'open' a file that's on the remote Win98 PC, there's no way to access it.  It doesn't appear in the list of locations available to me, and there's nowhere to manually enter a different location.[/QUOTE]
My bad.  I think you can do it in Nautilus, but it isn't universal in Gnome the way it is in KDE.  In KDE, the IOslaves make every KDE app network transparent.

---

### Post by Old *ix Geek on 2005-09-27
> do this

Code:

mount -t smb '\\server_by_IP_or_hostname\sharename' /mount_point/

THANK YOU!  That worked like a charm.  It prompted me for the Win98 box's password, and I'm now happily able to browse its contents from within applications.

---

