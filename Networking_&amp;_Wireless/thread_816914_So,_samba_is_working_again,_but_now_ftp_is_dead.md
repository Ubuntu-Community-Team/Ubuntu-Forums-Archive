---
title: "So, samba is working again, but now ftp is dead"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by tigrezno on 2008-06-03
Hi all, i've installed latests updates, and samba is working!

My problem now is my ftp server.

This is what i found:

  1) I can download files with no problem (at 100mbits)
  2) I can't upload files since they got stalled after some seconds (they start and a file is created on the server, so no permission issues here)

I've tested vsftpd and proftpd on the server side with the same result
I've tested nautilus-ftp, gftp and ftp-cmdline on client side with same result

Seems like kernel related.
Can you help me?

---

### Post by superprash2003 on 2008-06-03
is there enough space on that drive?? :D

---

### Post by tigrezno on 2008-06-03
> **superprash2003 said:**
> is there enough space on that drive?? :D

yes, of course:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   18G   17G  52% /

---

