---
title: "Problems Connecting to Samba Server"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by btrichardson on 2007-02-10
Hello all,

I have Ubuntu 6.06 Server installed on a machine along with Samba.  I have Samba configured and I can access it via an ssh tunnel from my XP machine using port forwarding.  However, I'm trying to connect to it with a laptop running Ubuntu 6.06 and I get the following:

```

btricha@Ubuntu:~$ sudo mount -t smbfs -o port=139 //192.168.192.251/btricha /mnt/smb/
timeout connecting to 192.168.192.251:139
Error connecting to 192.168.192.251 (Operation already in progress)
13857: Connection to 192.168.192.251 failed
SMB connection failed
btricha@Ubuntu:~$

```

Can anyone help me figure out what the problem is?!  Also, does anyone know why I can only connect to the Samba server from my XP machine if I go through an ssh tunnel?

Thanks in advance!

---

