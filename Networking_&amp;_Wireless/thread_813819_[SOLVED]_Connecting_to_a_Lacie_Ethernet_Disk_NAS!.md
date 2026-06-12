---
title: "[SOLVED] Connecting to a Lacie Ethernet Disk NAS!"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by Irwin J. Finster on 2008-05-31
Hi,

I got my hands cheaply on a Lacie Ethernet Disk NAS system it runs Windows embedded, but beggars can't be choosy.

What I want is to connect to this NAS, and have it avaliable on bootup to store my music collection. For Windows PC's lacie has a tool which lets me do this. But I donwloaded their manual, and it tells me to acces the disk with linux use samba.....great.... I have not the least clue how to do that.

Is there a graphical frontend to do this kind of stuff easily, or some kind of step by step guide on what to do?

Thanks for any Help,

Irwin

---

### Post by dmizer on 2008-05-31
to mount your nas from ubuntu with samba, see the second link in my sig.

---

### Post by Irwin J. Finster on 2008-06-01
Thanks a lot! I can recommend this guide to anyone who has a similar setup! Worked like a charm! :)

---

### Post by th00ht on 2010-05-01
Although this is a rather old thread it was the first one that popped up when I search specifically for mounting to a Lacie Etherdisk. Unfortunately the described routine does not work (in my case). I connected to my Lacie Etherdisk Mini using:```

sudo mount -t cifs //tethys/media /media/tethys-media/ -o username=j,password=*****,iocharset=utf8,file_mode=0777,dir_mode=077
```and using```
sudo mount -t cifs //tethys/media /media/tethys-media/ -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

In both cases write permissions were not allowed:```
mkdir /media/tethys-media/test
mkdir: cannot create directory `/media/tethys-media/test': Permission denied
```Interestingly any attempt to change the owner resulted in an error
```
[j@janus /]$ sudo chown nobody:nobody /media/tethys-media/video/
chown: changing ownership of `/media/tethys-media/video/': Input/output error
```
The user 'j' on the lacie drive does have write rights, if accessed from Microsoft Windows XP (tm) There seems to be no problem.

I'm puzzled

---

### Post by mip on 2010-07-26
I have a Lacie NAS at mylacie.local.

I'm trying to mount it using the following command:

```
mount -t cifs //mylacie.local/directory /media/share -o username=***,password=***,iocharset=utf8,file_mode=0777,dir_mode=0777
```

I'm getting the following error:

```

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

dmesg returns:

```

[13992.766847] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[13992.766857]  CIFS VFS: Send error in SessSetup = -13
[13992.766870]  CIFS VFS: cifs_mount failed w/return code = -13

```

Anyone have any ideas?

---

