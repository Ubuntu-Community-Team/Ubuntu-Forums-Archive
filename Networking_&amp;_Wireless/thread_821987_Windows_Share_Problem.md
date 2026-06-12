---
title: "Windows Share Problem"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by hmaich on 2008-06-07
Hello all,

I am having some problems trying to mount a windows share.
I've tried the command mount -t cifs //169.254.0.1/fotos /tmp/fotos/
  but I got the follow error: mount error 20 = Not a directory. 
The mount -t smbfs //169.254.0.1/fotos /tmp/fotos/
 gives me the same error message.
The problem is the fotos is a directory.

I've tried to use the “Connect to Server” in the Places menu then select “Windows Share” and fill out the IP and the directory and it works without problems, but this way I cannot access this mount in the command line.

Does anyone know how can I mount this drivers in command line or how can I get the performed command used by the “Connect to Server” to perform it on the command line?

Thanks in advance.

---

### Post by superprash2003 on 2008-06-07
169.254.x.x is a default ip which you get when you dont get an ip via DHCP.. it wont work like that..go to the command prompt and type ipconfig and post screenshot here so that you can find out what the actual windows ip is

---

### Post by hmaich on 2008-06-14
Hello,

It is true. So I configured other IP. Now it is 192.168.178.22 and still doing the same. I can access everything by the "Connect to Server" but I can't mount it in command line.

Any idea??

Thanks

---

