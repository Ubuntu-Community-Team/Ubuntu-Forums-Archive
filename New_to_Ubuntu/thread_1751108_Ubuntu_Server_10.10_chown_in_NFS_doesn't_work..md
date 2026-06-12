---
title: "Ubuntu Server 10.10: chown in NFS doesn't work."
date: 2011-05-06
forum: New to Ubuntu
---

### Post by _sphinx_ on 2011-05-06
Hi,

I have create a NFS server (IP: 192.168.2.3) with following export configuration at /etc/exports:

```
/srv/cloud 192.168.2.4(rw,async,no_subtree_check,no_root_squash)
```

From machine 192.168.2.4 I have following configuration in /etc/fstab:

```
192.168.2.3:/srv/cloud  /srv/cloud      nfs     rw,hard,intr    0       0
```

Now from machine 192.168.2.4 with root user, I create a file "/srv/cloud/xyz" and then change the ownership of the file to user "oneadmin". I have following commands and the error in the output:

```
#touch /srv/cloud/xyz
#chown oneadmin:oneadmin /srv/cloud/xyz
chown: changing ownership of `xyz': Invalid argument
```

I have user "oneadmin" at both server and the client machine with same user and group id:

At client:
```
#id oneadmin
uid=9000(oneadmin) gid=9000(oneadmin) groups=9000(oneadmin),110(libvirtd)
```

At server:
```
#id oneadmin
uid=9000(oneadmin) gid=9000(oneadmin) groups=9000(oneadmin)
```

What could be the problem in changing the ownership of the file from the root user at nfs client machine when "no_root_squash" has been specified?

Regards,
Amit

---

### Post by gmargo on 2011-05-06
Interesting problem; I duplicated it using a 10.10 Maverick server and 11.04 Natty client.

I think it has to do with NFS version 4.  The server's files are created with the correct user id, but the client always shows a "unknown user/group" uid/gid for the files and directories.

When I forced the client to use NFS version 3, then everything worked as expected.  To do this, add "vers=3" to the nfs mount options in the client's /etc/fstab.
```

192.168.2.3:/srv/cloud  /srv/cloud      nfs     rw,hard,intr,vers=3    0       0

```But why doesn't NFS version 4 work as expected?

---

