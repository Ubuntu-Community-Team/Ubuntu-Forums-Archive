---
title: "NFS permissions for mounting over ssh"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by bill-linux on 2007-02-25
I am running Ubunutu 6.06 LTS. It has two users: superuser and bill -- bill has fewer permissions in general than superuser, which is the user created when installing ubuntu.

Bill owns the following directory: /home/bill/homefiles.  Then this is mounted to the files on another server by nfs via an ssh tunnel. The problem: When the share is mounted to /home/bill/homefiles the owner of all the files becomes superuser. Why is this? For several years now I've used this same mounting on a Debian Sage installation and never had this permissions issue. What permissions should I be looking at? The  nfs server has the correct ones -- since it works currently on another client. This would lead me to believe it was client side. It would seem that Ubuntu has something set up slightly differently. Any suggestions for where to look?

---

### Post by bill-linux on 2007-03-01
PROBLEM SOLVED: NFS depend on the UID (User ID number), and not on the login id. If one examines /etc/passwd, for example, you'll see entries like this:

bill:x:1001:1001:Bill Jones,,,;/home/bill:/bin/bash

That first number indicates the UserID. It appears that the first account you create is given UID 1000, the second UID 1001, etc. On my NFS server I created bill first and it was given a UID of 1000; on my client I created bill SECOND and it was given UID 1001, the login "superuser" was created first and given a UID of 1000. Thus when by client mounted the nfs directories it assigned the files to "superuser." Therefore I had to change the UID of superuser to 1002, and the assigned "bill" to 1000. To do this you need to 1) change the UID, and then 2) change the UID of the files owned by the OLDUID.

usermod -u NEWUID LOGIN
then to change ownership of the files
find / -user OLDUID -print -exec chown NEWUID {} \;

REFERENCES: 

Good article on NFS permissions (UID, GID)
[http://www.troubleshooters.com/linux/nfs.htm#_If_it_mounts_but_cant_access](http://www.troubleshooters.com/linux/nfs.htm#_If_it_mounts_but_cant_access)

Changing UID
[http://www.sunmanagers.org/archives/1997/0005.html](http://www.sunmanagers.org/archives/1997/0005.html)

---

