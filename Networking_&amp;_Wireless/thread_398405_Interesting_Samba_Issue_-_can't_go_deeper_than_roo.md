---
title: "Interesting Samba Issue - can't go deeper than root of share"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by scott212 on 2007-04-01
Hey gang, curious as to why I can connect to a local samba share and browse the root of the shared directory, but when I try to go even one directory deeper, it fails. I don't get an error message and the prompt shows that I'm in that deeper directory, but it still shows the outer directories contents. Any ideas? Everything works as expected when accessed from OSX. I'm trying to access it from ubuntu 6.10 (edgy eft).

samba 3.0.2

---

### Post by likwid on 2007-04-01
It sounds like you have permissions to execute the child folder but once there you don't have permission to read its contents. Check the permissions at the server using "ls -l" <folder>. Maybe add yourself to the same group as the file creator (user)?

---

### Post by scott212 on 2007-04-01
I thought about that too, but I'm not so sure I can do much about that. The samba share is actually built into one of those Linksys routers with 'Storage Link'. I've got read and write set for the group that I'm in, but the problem mentioned earlier persists. In the setup dialog, 'execute' does not exist. The OSX account is in the same group with the same permissions and works just fine. So it's gotta be something with edgy.

---

### Post by likwid on 2007-04-02
Have you tried mounting the share?

An example fstab entry:

//media/Shared	/mnt/Shared		cifs		credentials=/root/.smbcredentials,iocharset=utf8,**file_mode=0665,dir_mode=0771** 0 0

---

