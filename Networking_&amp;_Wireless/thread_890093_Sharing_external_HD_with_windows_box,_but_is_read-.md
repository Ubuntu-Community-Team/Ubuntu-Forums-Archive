---
title: "Sharing external HD with windows box, but is read-only..."
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by Zuuted on 2008-08-14
I have setup an external hard drive on a laptop running Ubuntu Studio v8.04.1 to network & share with Win XP pro. Have installed/configured samba, and setup "net usershare"... all shows up fine except that the windows machine can only view the external HD as read-only, cannot modify files whatsoever. /etc/samba/smb.conf look all good and chmod shows the root of the external HD as RWX but the windows comp still cant write to it.

Please help!
Thanks in advance...

---

### Post by Zuuted on 2008-08-16
Come on, someone around here has gotta know how to fix this... 
It seems to me that i'm just missing some simple permissions settings or something.

When I run the command "ls -d -l" it shows only drwx------ permissions... how can I set it to drwxrwxrwx ???
The external HD needs to be writable over the entire network, including linux and windows computers.

---

### Post by linuxvacuum on 2008-08-18
If you want to give ALL permissions to EVERYONE (which is really not secure) use the following command :

> sudo chmod -R 777 /dev/sdb1

Assuming that the partition of your external hard drive is /dev/sdb1. Again this will give FULL access to ANYONE of ALL the files on your hard drive.

---

### Post by Zuuted on 2008-09-13
Thanks!
Got it fixed though...
The 777 parameter was the missing variable. ;)
It is a closed network, so that is exactly what was needed.

---

