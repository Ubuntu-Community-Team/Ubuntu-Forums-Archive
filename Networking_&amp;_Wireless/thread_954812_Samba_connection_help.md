---
title: "Samba connection help"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by stevenhp1987 on 2008-10-21
Hello, one of my friends has set up a samba file share in a house running under freenas.

I am trying to mount it automatically so that I can let amarok create a collection from the media share.

I have tried how-to's that I have found and cannot create a mount point. The folder i'm trying to connect to is:

smb://192.168.42.100/450%20gb/

Well its 450 gb, but nautilus has made it look like the above due to the space.

I have no idea, have tried many stuff found on here to no luck, I have tried this:

sudo mount -t cifs //192.168.42.100/450%20gb /media/server

I'm trying to mount to /media/server

it keeps coming up with this error:

mount: wrong fs type, bad option, bad superblock on //192.168.42.100/450%020gb,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I have no idea what to do :/

Can anybody help, cheers (it has no user/name or pass on the server btw).

---

### Post by stevenhp1987 on 2008-10-25
Can anybody help, I am stuck as to what to do?

---

### Post by vanadium on 2008-10-25
```
sudo mount -t cifs //192.168.42.100/450%20gb /media/server

```

Under the shell, you should type the space:

```
sudo mount -t cifs //192.168.42.100/450\ gb /media/server

```

However, check wether a directory "450 gb" will effectively exist on the server: seems a strange name for a folder to me.

---

