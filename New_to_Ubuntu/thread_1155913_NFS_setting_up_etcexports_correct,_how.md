---
title: "NFS setting up /etc/exports correct, how?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by SpinningAround on 2009-05-11
I'm about to share files on my local network using NFS but can't set up /etc/exports correct

I would like to share '/home/ubuntu/share/' with the following IP 192.168.1.1 192.168.1.5 192.168.1.7 but don't know how. Also I would like to give these computers the ability to read and write files but not to execute them. Then is the tricky part with giving the right privileges in 'hostname1(rw,*,*,*) I'm aware that this can be dangerous if done wrong.

---

### Post by superprash2003 on 2009-05-11
hope this helps [http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

---

