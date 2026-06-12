---
title: "GmailFS '302' error"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by Martje_001 on 2008-01-05
Hello,
After following [this]("https://wiki.ubuntu.com/GmailFS") guide I ran
```
mount -a
```
This was the output:
```
Ignored option :rw
HTTP Error 302: The HTTP server returned a redirect error that would lead to an infinite loop.
The last 30x error message was:
Moved Temporarily

```
Does anybody know what's going on? Thank in advance!

---

### Post by MrFSL on 2008-01-05
Please post the output of:
```
cat /etc/fstab
```

---

### Post by Martje_001 on 2008-01-05
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=926210e2-a0bf-4641-bd46-b6e12ed799a1 /               ext3    defaults,errors=remount-ro 0       0
# /dev/hda1
#UUID=E840C63C40C6116C /media/hda1     ntfs    defaults,umask=007,gid=46 0       0
# /dev/hda5
UUID=94ec8fd1-67ae-456a-8b2c-da0cac22a3a9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/home/martin/Muziek /home/manon/Muziek none bind
/home/martin/Muziek /home/marieke/Muziek none bind
/usr/share/pycentral/gmailfs/site-packages/gmailfs.py /media/xxxxx gmailfs username=xxx,password=xxx,fsname=xxx
```

---

### Post by Mark Nikkels on 2008-01-10
I am getting the same error. Tried everything, from upgrading packages (even experimental)

HTTP Error 302: The HTTP server returned a redirect error that would lead to an infinite loop.
The last 30x error message was:
Moved Temporarily

The gmailfs.log contains:
01/10/08 22:07:13 ERROR      OpenSSLProxy is missing. Can't use HTTPS proxy!
01/10/08 22:07:13 INFO       Starting gmailfs in child process (PID 22608)
01/10/08 22:07:13 INFO       Mountpoint: /home/mrnikk/gmail
01/10/08 22:07:13 INFO       Named mount options: {'username': 'mail2intohair', 'password': '********', 'fsname': 'RNjdzTNC'}
01/10/08 22:07:13 INFO       waiting for /home/mrnikk/gmail to become a mountpoint
01/10/08 22:07:20 INFO       Connected to gmail
01/10/08 22:07:20 DEBUG      get stat:/
01/10/08 22:07:20 DEBUG      check getnodemsg:/
01/10/08 22:07:20 DEBUG      ind:0
01/10/08 22:07:20 DEBUG      dirpath:/ name:
01/10/08 22:07:21 DEBUG      ind:0
01/10/08 22:07:21 DEBUG      dirpath:/ name:
01/10/08 22:07:21 INFO       Sent message failed
01/10/08 22:07:21 INFO       Sent message failed
01/10/08 22:07:21 INFO       Sent message failed
01/10/08 22:07:21 ERROR      Send failed too many times
01/10/08 22:07:21 ERROR      gmailfs child died, exiting...
01/10/08 22:07:28 INFO       gmailfs terminated

What contains your gmail.log? (set logging to DEBUG in /etc/gmailfs/gmailfs.conf)

As you can see connection is working. Sending a message fails. Big Question: WHY?

To use GMail as a file-system, I now use the plugin GSpace for FireFox.
Works like a charm, but I still want to know wat&#347; wrong with mounting in my filesystem.

Hopefully someone can give an answer on that.

Mark.

---

### Post by Rippy on 2008-02-02
I'm getting the same problem. Hopefully someone knows a fix for it.

---

