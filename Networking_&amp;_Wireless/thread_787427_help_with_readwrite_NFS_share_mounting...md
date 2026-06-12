---
title: "help with read/write NFS share mounting.."
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Geran on 2008-05-08
Hi,

I've been trying for quite a while now to get full access to my nfs shares, but I have only been able to get read-only access so far. I need to be able to make files, folders, and edit files already in.

Currently, my /etc/exports on the server....

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
/home/gsmith/nfs_desktop 10.0.0.0/24(rw,async,no_root_squash)
/home/gsmith/mysql_tables 10.0.0.0/24(rw,async,no_root_squash)

I have been trying to edit it to get the desired results a few times, but no luck yet, any help is greatly appreciated :).

---

### Post by ivom on 2008-05-08
I am not an export in this area, but from my experience with NFS (if you are not using nis, but just regular NFS mounting), in order to have the read/write access you need to have the same user id and group id on both computers (local and remote PC or host and guest machines if you are running VMs). 

Try this: 
# id
uid=1000(your_name) gid=1000(your_name) ...

and try to match the "uid" and "gid" numbers on both machines (your group name does not necessary have to be the same as username, but they have to match on both machines). 

To change these numbers, you can edit /etc/passwd file: 

your_name: x:1000:1000:.....

---

