---
title: "Samba vexes me"
date: 2004-12-06
forum: Networking &amp; Wireless
---

### Post by negativ on 2004-12-06
Using Hoary.

Windows can see, browse, and read/write linux no problem.  Linux (more specifically, Nautilus) can see windows shared directories, but cannot see anything in the directories.  I just get throbbing toes and and empty window forever and ever.

However, if I open a terminal and do 
```
smbclient //windowshostname/share
```
I can see, browse, and read/write in the terminal.  Is this a misconfiguration on my part, or a bug somewhere?

Also, I can't mount shared windows directories at all.
```
 *$ sudo mount //windowshost/share /mnt/windowsshare -t smbfs*
mount: wrong fs type, bad option, bad superblock on //windowshost/share,
       missing codepage, or too many mounted file systems
```

So... what do I do?

---

### Post by WorLord on 2004-12-07
Bump (Using Warty)

---

### Post by triad169 on 2004-12-10
Do u have smbfs installed?

I mount windows share like this:

smbmount //windows_machine/share /local_mount_point -o username=username%password,fmask=644,dmask=755,uid=1000,gid=100,ip=ip_address, debug=0,workgroup=workgroup_name

Actually I put this in a script and run when I  need access.

Hope this helps.

---

