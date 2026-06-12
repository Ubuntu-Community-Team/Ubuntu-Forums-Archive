---
title: "[SOLVED] mount.cifs with sec=ntlmv2i"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by jakyra_1 on 2008-10-14
I'm an old Fedora user and I came over to Ubuntu somewhat unexpectedly and I'm trying to re-create everything that I had set up before. 

I'm trying to mount a connection to a Windows server that requires ntmlv2i to connect. I've been googling this for a day now and there is very little in the way of search results and I don't understand enough of the results to know if they apply to my situation.

I'm using Hardy Heron. Code and errors below.

```

joelle@joelle:~$ sudo mount -t cifs //our.domain.com/c$ /media/production -o username=joelle,iocharset=utf8,file_mode=0777,dir_mode=0777,sec=ntlmv2i
Password: 
mount error 95 = Operation not supported
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
joelle@joelle:~$ mount.cifs --version
mount.cifs version: 1.10-3.0.28a
joelle@joelle:~$ uname -r
2.6.24-19-generic
joelle@joelle:~$ sudo echo 0x4004 > /proc/fs/cifs/SecurityFlags
bash: /proc/fs/cifs/SecurityFlags: Permission denied

```

How do I either get a version of mount.cifs that supports ntlmv2i or edit the SecurityFlags?

Thanks much!

---

### Post by cariboo on 2008-10-14
I use smbfs to mount my shares manually:

```
sudo mount //willy/music /media/music
Password: 
jim@intrepid:/media$ 
```

with this result:

```
//willy/music         367G  286G   82G  78% /media/music
```

Jim

---

### Post by jakyra_1 on 2008-10-15
> **cariboo907 said:**
> I use smbfs to mount my shares manually:

```
sudo mount //willy/music /media/music
Password: 
jim@intrepid:/media$ 
```

with this result:

```
//willy/music         367G  286G   82G  78% /media/music
```

Jim

This doesn't work for me.

```
joelle@wjoelle:~$  sudo mount //our.domain.com/c$ /media/production
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

I am connecting to a windows box and the administrators told me that I have to use ntlmv2i to connect.

Thanks!

---

### Post by jakyra_1 on 2008-10-15
I figured this out with some guidance from a friend. 

For some reason using a credentials file made all of the difference in the world. With the credentials file it worked flawlessly without the nlmv2i option.

---

### Post by dmizer on 2008-10-15
If this issue is solved now, please use the "Thread Tools" menu to mark this thread as "solved".

Thank you.

---

### Post by jakyra_1 on 2008-11-03
Actually I ended up having a few problems with this still.

I played around with it and what I ended up doing was this:

```
//windows.server.com/e$    /media/production        cifs    credentials=/root/.smbcreds_prod,iocharset=utf8,file_mode=0777,dir_mode=0777,gid=smb,uid=jakyra,rw,sec=ntlmv2 0 0

```

I used [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534) heavily. But I also found that I had to set a the gid and uid to get full read/write access. but maybe that's because they're not mounted in my home directory. 

I thought it was odd that on fedora I had to use ntlmv2i but on ubuntu I could use ntlmv2. 

Hope this helps someone else.

---

