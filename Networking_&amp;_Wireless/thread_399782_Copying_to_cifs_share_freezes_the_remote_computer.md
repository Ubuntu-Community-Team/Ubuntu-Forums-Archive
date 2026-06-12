---
title: "Copying to cifs share freezes the remote computer"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by luvona2000 on 2007-04-02
Hello Dear All,

I would like to ask your advices with the following problem:
The share folder from Windows 2000 Server SP 4 is mounted on the Ubuntu 6.10 machine using the following string in fstab:
//winserver/share$ /mnt/share cifs credentials=/etc/credentials,uid=0,gid=0,domain=mydomain  0 0
There is no problem with browsing this share, but when I’m trying to copy file from Ubuntu machine to Windows 2000 using cp it totally hangs the remote host.  File size is around 1GB, there is enough space on Windows machine. I was able to copy the same file to Windows XP from Ubuntu machine without any problem.
Searching Internet I saw people having similar problem but unfortunately I wasn’t able to find any solution.

Thank you very much for your help,
L

---

