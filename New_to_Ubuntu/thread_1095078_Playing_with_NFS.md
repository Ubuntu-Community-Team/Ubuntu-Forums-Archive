---
title: "Playing with NFS"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-13
Hi,

I'm connecting to a server on internal network from my desktop. I'm following [http://nfs.sourceforge.net/nfs-howto/ar01s06.html]("http://nfs.sourceforge.net/nfs-howto/ar01s06.html") to make the connection secure.

Just wanted to check whether this may have effect on any other service. I currently run ftp from the server and plan later lamp/webserver and ldap. Do either of those use portmap et. al that would cause me problems.

Currently I've got hosts.deny
> 
portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL

Then allow myinternal ip.

Thanks in advance



Rich

---

