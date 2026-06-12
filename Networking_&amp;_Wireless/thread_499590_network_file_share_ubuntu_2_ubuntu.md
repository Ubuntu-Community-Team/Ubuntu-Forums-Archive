---
title: "network file share ubuntu 2 ubuntu ?"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2007-07-12
I shared the folder and the picture shows what I used as ip was 192.168.100.1
Is this the IP of the machine on the network you want to allow in to the files?

However in the places network, the machine shows up but no folders appear.

---

### Post by sj3fk3 on 2007-07-13
> **sdowney717 said:**
> I shared the folder and the picture shows what I used as ip was 192.168.100.1
Is this the IP of the machine on the network you want to allow in to the files?

Yes

> **sdowney717 said:**
> 
However in the places network, the machine shows up but no folders appear.
The folder will only show up if you use 'Windows style' sharing. You should be able to connect to the folder using mount machine-ip:/home/scott.Music /mountpoint

If you use samba (Windows style sharing) the security is user based instead of IP.

---

### Post by sdowney717 on 2007-07-13
thank you very much, that works.

How about how do you know which folders on you computer are shared? there is no obvious appearance diff when viewed.

---

### Post by sj3fk3 on 2007-07-13
> **sdowney717 said:**
> thank you very much, that works.

How about how do you know which folders on you computer are shared? there is no obvious appearance diff when viewed.

For nfs shares see /etc/exports, samba /etc/samba/smb.conf

---

