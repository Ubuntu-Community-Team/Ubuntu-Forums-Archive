---
title: "nfs share problem"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by kopolov on 2011-08-25
I'm trying to create nfs share on a server.
I am able to mount it, but it is set with permission for "nobody" and "nogroup" user/group.

My goal it to create 2 share points for 2 users we have on our machines.
Each user will access its own space on the server.

Here is the line which is in the /etc/exports file on the server:
/srv/nfs4/nurit	*(async,insecure,no_root_squash,rw,nohide)

Here is the line on the client side (/etc/fstab):
logan:/srv/nfs4/nurit /home/nurit/test nfs4 auto,rw 0 0

also, here is line from the "mtab" (server side):
/home/nurit /srv/nfs4/nurit none rw,bind 0 0
(its binded with rw permissions)

("logan" is the server name)

client: ubuntu desktop 11.04
server: ubuntu server 11.04

no firewall, proxies, etc ...

I am able to mount, but can't make it with write permission.

The permission on the mount point (server side) are 755.

what am I missing here?

Hagai

---

### Post by soldersplash on 2011-08-25
What permissions and ownership exist on the server side for the path you are exporting?

---

### Post by SeijiSensei on 2011-08-25
What are the permissions on the mount point?  What if you make the mount point owned by root.root?  I mount /home from my NFS server to /media/myserver at boot with root as the owner and group of the mount point.  As long as the password and group files are identical on both machines, user1 has full access to /media/myserver/user1, user2 has full access to /media/myserver/user2, etc.

You need "no_root_squash" to make this work, but it appears your server is configured that way already.

---

