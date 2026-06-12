---
title: "how can I mount NFS Share as root?"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by markosjal on 2014-03-13
I want to set up an NFS share i ubuntu 12.04 and mount it from a client as root.  To be clear, I need apps not running as root on client machine to be able to write files   so that the owner will show as root on server and client can read all files as root. I want to force the seever as always seeting thise reads writes from that client as root , regardless of user on client.


I need to do this all through /etc/exports on server and /etc/fstab on client

I have been struggling with this for days and could really uses some guidance. 

Thanks in advance

---

### Post by xicarusx on 2014-03-13
The only way to do this would be to allow rw and only use the mount as root. 

Instead an easier approach would be to use SAMBA and directory/file creation masks.

---

### Post by lukeiamyourfather on 2014-03-13
A better option might be to set ownership to nobody and nogroup for the shared files and then squash all in the NFS configuration (defaults to nobody and nogroup). If you really must use root then you can squash all and specify the user as root (not recommended).

---

### Post by SeijiSensei on 2014-03-13
The key requirement is adding "no_root_squash" to the list of options for the share in /etc/exports.

---

### Post by markosjal on 2014-03-13
Thanks to all of you. My current scenario is like this. I have an app running as "root" on server. I can not change this. I have a similar app running under user space on client. They share all data files via NFS

From the client if I log in as root then cd to the NFS mount I can then read/write as root on the shared NFS mount (server confirms files as owner root). If however I log in as user on the client, I no longer can read/write as root. Instead it seems to map to the user of the corresponding user ID (number)   .

I want to be able to log in to the client as user and maintain the ability to read/write the NFS share as root

current export is like this
```

/home/serverusername/  *(rw,async,no_root_squash,no_subtree_check)

```
I mount it on the client like this
```

192.168.1.2:/home/serverusername               /home/clientusername               nfs     _netdev,defaults,user,auto,noatime,intr   0 0

```



so if I change the export as follows
```

/home/serverusername/  *(rw,async,root_squash,no_subtree_check)

```

Then how do I define to squash all access to "root"?

I can not change how the server writyes these files. They will always be root:root


although the smb suggestion is good, I thought about it already and unfortunately I do not really see it as a viable option for performance reasons.

---

### Post by bab1 on 2014-03-13
> **markosjal said:**
> Thanks to all of you. My current scenario is like this. I have an app running as "root" on server. I can not change this. I have a similar app running under user space on client. They share all data files via NFS

From the client if I log in as root then cd to the NFS mount I can then read/write as root on the shared NFS mount (server confirms files as owner root). If however I log in as user on the client, I no longer can read/write as root. Instead it seems to map to the user of the corresponding user ID (number)   .

I want to be able to log in to the client as user and maintain the ability to read/write the NFS share as root

current export is like this
```

/home/serverusername/  *(rw,async,no_root_squash,no_subtree_check)

```
I mount it on the client like this
```

192.168.1.2:/home/serverusername               /home/clientusername               nfs     _netdev,defaults,user,auto,noatime,intr   0 0

```



so if I change the export as follows
```

/home/serverusername/  *(rw,async,root_squash,no_subtree_check)

```

Then how do I define to squash all access to "root"?

I can not change how the server writyes these files. They will always be root:root


although the smb suggestion is good, I thought about it already and unfortunately I do not really see it as a viable option for performance reasons.

Set the group ownership to a common user.  I use the user group named *users *.  This is gid 100.  You need to set inheritance on the *basedir* of the export by using chmod 775.  At this point it doesn't matter if the root user or a mortal user creates or modifies the file the ownership is always root:users with the directory perms of 775 and file perms of 664.

---

### Post by markosjal on 2014-03-13
Thanks I finally figured out another work-around that I think is working. 

I ran the program as root on the client system and so far so good. 

I question the implications of root:users but might try it if what I have does not work

---

### Post by bab1 on 2014-03-13
> **markosjal said:**
> I question the implications of root:users but might try it if what I have does not work
What implications are those?  This is the standard method of accommodating multiple users in UNIX (Solaris and BSD's) and versions of Linux.  

Debian uses User Private Groups (UPG), but it is not viable scheme if you have multiple users accessing the same data.  Maybe [this]("https://security.ias.edu/how-and-why-user-private-groups-unix") will help in understanding the situation.  Running a process as root is far more dangerous from a system admin's point of view.

[COLOR="#0000FF"]**EDIT: **While this is a modification to the default method of UPG, it is not a *workaround *at all.  It is more like reverting to the UNIX/BSD way on a specific branch of the file system.[/COLOR]

---

