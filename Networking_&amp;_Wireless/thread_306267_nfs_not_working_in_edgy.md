---
title: "nfs not working in edgy"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by lime4x4 on 2006-11-24
I select nfs for my shares but i can't access them from another computer
as u can see in the following list there are being mounted.But i'm unable to view them from the specified computer
ohn@mythtv:~$ cat /etc/exports
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/media          192.168.0.11(rw)
/home/mythtv    192.168.0.11(rw)
/media/sda1     192.168.0.11(rw)
john@mythtv:~$

---

### Post by FrodoB on 2006-11-24
Have you installed the nfs server package? 

Most Linux distros do not come with nfs installed for security reasons.

There is a kernel nfs server and a user space nfs server.

Kernel:
$ sudo apt-get update
$ sudo apt-get install nfs-kernel-server

User Mode:
$ sudo apt-get update
$ sudo apt-get install nfs-user-server

I have never used the kernel mode server, but either one should work. And if one does not work remove it and install the other.

---

### Post by lime4x4 on 2006-11-24
i installed the user mode one i will uninstall and try the kernel one

---

