---
title: "&quot;Unable to mount UDF Volume&quot; trying to read a CD-ROM"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by sezzme on 2009-03-14
I have 2 CD-ROMs, both ordinary data cds, one burnt in xp, one in vista.  Windows can see these CDs fine, so can my friend's Mac.

My Ubuntu 8.10 will not mount these CDs.

This is an IBM P4 that is able to at least see burned live CDs  - just not data CDs.

Errors that come up:

Unable to mount UDF Volume:  DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I just want to get some txt and .mov files off these CDs onto my desktop.

This is not a networked computer.

Is there a patch I can download or what?

---

### Post by 73ckn797 on 2009-03-19
I do not know if there is a "UDF" format reader available for Linux systems. You will have to "Google" to find something. I have had this problem under Windows and have to install a UDF reader. Mine were always written using Nero. You may need to copy the files off of the disk in Windows and make a simple data disk on a CD-R disk or copy to a usb flash stick to move to Ubuntu. I did just this when I wanted to put some docs into Ubuntu that I backed up to a CD-RW disk from years ago.

---

### Post by ufuxlinux on 2009-03-19
As far as I know, from my experiences, CDs that burned with some windoz media player and stuff like these, can not be mounted in Linux distros, and returns error like that.

---

### Post by mescobal on 2010-10-29
You can use:

sudo mount -t iso9660,udf /dev/xxx /yyy/zzz

where xxx is your DVD (you can check it with System -> Administration -> Disk utils) and /yyy/zzz is the place where you want the files to be mounted.

Marcelo.

---

