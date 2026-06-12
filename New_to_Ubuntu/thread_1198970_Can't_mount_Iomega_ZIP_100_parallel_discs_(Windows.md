---
title: "Can't mount Iomega ZIP 100 parallel discs (Windows formatted)"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Manoel on 2009-06-28
Hi, there. First I must apologize if I don't include all necessary info about my problem... I'm new to this forum and quite new to Linux as well.

I'm trying to use my old Iomega ZIP discs, which were formatted using an also old **Windows 95**, now with my Ubuntu 8.10.

After a while reading old posts on the WWW, I happened to find this brief tutorial: [https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive) 

I followed the simple instructions for 8.10 but though I could see my ZIP unit with Nautilus I could not reach ZIP files contents. Nautilus shows nothing when click on the ZIP unit, and when I try to eject disc says that cant' mount disc and possibly there's no disc inside the unit. After a while I get this **error** too:

> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.I'm trying everything as root, just to minimize permissions-related problems.

As I don't get simple instructions in [https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive) to work, I tried the long ones. But no way! :-(

I also read that **ppa** and **sg** sould be loaded before **lp** so I moved them up in my /etc/modules and reboot. It does not work either.

I've also tried to look for ZIP file with my **Disk Manager** tool: [http://flomertens.free.fr/disk-manager/](http://flomertens.free.fr/disk-manager/) but ZIP drive is not there for this manager.

I've tried **fdisk -l** but no disk ending in 4 is there (I've read at [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131) and somewhere else that ZIP files formated with Windows has to be named with 4 because somthing related to partition-style of this disks).

I've tried to mount manually like [https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive) explains but I could not and received an error message.

:confused:

So I'm at a lost. 

I have seen posts in this forum from [users that did not have any problems]("http://ubuntuforums.org/showthread.php?t=1012816") and for them it was just nearly plug-n-play with their ZIP parallel units. Why not me? I don't know! Could some one please help?

Thanks in advance.

---

### Post by Manoel on 2009-06-28
> **Manoel said:**
> I've tried to mount manually like [https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive) explains but I could not and received an error message.

I forgot to tell which was the error I get (I'll try to translate it back because I have Spanish language Ubuntu):

> mount:  block device /dev/sda4 write-protected; mounting read-only
mount: you must specify the filesystem type

---

