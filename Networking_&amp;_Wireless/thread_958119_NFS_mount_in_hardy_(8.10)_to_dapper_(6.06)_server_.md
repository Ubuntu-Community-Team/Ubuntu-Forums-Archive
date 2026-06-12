---
title: "NFS mount in hardy (8.10) to dapper (6.06) server group permissions issue"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by bojo on 2008-10-25
I am using hardy to mount a share from 6.06 server using NFS.
-- from fstab --
turtle:/home/bb_family  /mnt/netshares/turtle_bb_family nfs     rsize=8192,wsize=8192,timeo=14,intr
--
everything is correct EXEPT...

I have RW permissions to a folder (not as a owner but I am part of the group)

Locally everything is ok - I can create and delete files
over the NFS I can not create and delete files.

The above did work when both systems were 6.06 (dapper) and when I upgraded (fresh install) Hardy it does not work any more.

The permissions for all users were preserved - so user that is 1001 on first system is the same UID on the second system for all the users

the server is turtle
--
root@turtle:/home/bb_family/temp# ls -ln
total 4
drwxrwxr-x 2 1003 1003 4096 2008-10-24 22:08 permcheck
root@turtle:/home/bb_family/temp# 
--
the client is eagle
root@eagle:/home/bb_family/temp# ls -ln
total 152400
drwxrwxr-x 2 1003 1003     4096 2008-10-24 22:19 permcheck
--
I am user 1001 and am part of group 1003
when I mount turtle over NFS the system will deny access for RW to the folder however I have no issues when I stay on the local system (eagle).

Any help will be appreciated.

---

