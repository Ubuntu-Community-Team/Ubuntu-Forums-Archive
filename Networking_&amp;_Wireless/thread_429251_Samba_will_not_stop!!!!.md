---
title: "Samba will not stop!!!!"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by kvonb on 2007-05-01
I have 6.10 on my server, and for some reason when I try to stop samba with:

```
 sudo /etc/init.d/samba stop
```

....the bloody thing keeps going!

I do a ps list and it shows 3 instances of /usr/sbin/smbd -D running, I try to kill them but they keep coming back!

It seems to start having problems when I enable another share through either right clicking and selecting "share", or editing smb.conf to add a new share, or even changeing an existing path.

I have to reboot the server to get it working properly again!

Anyone come across this before?

---

### Post by kvonb on 2007-05-01
OK, getting somewhere at last.

I did:

```
sudo kill -9 <process number>
```

on each of the smbd instances, then started samba again with:

```
sudo /etc/init.d/samba start

```
It seems to be running properly now.

The thing is that there are still 2 instances of smbd running, and one nmbd.  Why 2?

---

