---
title: "Printing problems XP to Ubuntu 8.10"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-01-27
I have an XP machine linked wirelessly to my Ubuntu machine via Samba. Both are on a MS Network called MSHOME. On the XP machine I can see the Ubuntu machine but not the printer. I can print a test page from the XP machine using CUPS....but I cannot install the printer as an internet printer for the XP machine. I thought the problem was on the XP side....but now I am not so sure.When I look up Network in Ubuntu I can find both machines..and even access the XP machine...but the Ubuntu machine does not show any attached printer etc. I can print with the Ubuntu machine as the printer is directly attached to that machine. When I look at the permissioning for MSHOME, it says "could not be determined".

There is something really simple here that I am missing.....any idea what it might be?

This comes from the Syslog..I am not sure if it is relevant...

Jan 27 20:52:53 PJKING kernel: [97451.629623] type=1503 audit(1233042773.527:28): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4843 profile="/usr/sbin/cupsd"
Jan 27 20:53:20 PJKING kernel: [97478.291604] type=1503 audit(1233042800.187:29): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4843 profile="/usr/sbin/cupsd"
Jan 27 20:53:20 PJKING kernel: [97478.296692] type=1503 audit(1233042800.195:30): operation="inode_permission" requested_mask="rw::" denied_mask="rw::" fsuid=0 name="/var/lib/samba/group_mapping.ldb" pid=4843 profile="/usr/sbin/cupsd"
Jan 27 21:04:01 PJKING kernel: [98119.531706] type=1503 audit(1233043441.427:31): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=20444 profile="/usr/sbin/cupsd"

---

### Post by matrixblue on 2009-04-18
Try this out [http://www.linuxforums.org/forum/ubuntu-help/71194-sharing-printer-between-win-lin.html](http://www.linuxforums.org/forum/ubuntu-help/71194-sharing-printer-between-win-lin.html)

---

### Post by cariboo on 2009-04-18
Have a look at my screenshot and make sure **Share published printers connected to this system** is enabled. To get to the cups web management interface type:

```
http://localhost:631
```

in the firefox address bar.

Jim

---

### Post by dunbrokin on 2009-04-19
Thanks all....

---

