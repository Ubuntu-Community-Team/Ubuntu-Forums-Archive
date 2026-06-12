---
title: "Running NFS under Ubuntu 8.04"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by tarek.elsherbiny on 2009-02-08
I am starting embedded Linux project and I need to run NFS server on my Laptop (NFS server) under Ubuntu 8.04.
I have installed NFS server on ubuntu and I am sure the client is running on the target board.
I tried to follow the steps in this link

[http://www.troubleshooters.com/linux/nfs.htm](http://www.troubleshooters.com/linux/nfs.htm)

but I get some errors like portmap 3:off 4:off 5:off
and nfs no such serves 

Is there any tutorial that explains nfs for ubuntu ?

Thanks

---

### Post by ibutho on 2009-02-08
Try this [guide]("http://www.howtoforge.com/nfs-server-and-client-debian-etch"). Its for Debian, but I am sure it will work fine for Ubuntu.

---

### Post by tarek.elsherbiny on 2009-02-09
I tried the link but I get this error:

 mount -t nfs 10.10.10.1:/nfs /mnt/nfs                     
portmap: server localhost not responding, timed out                             
RPC: failed to contact portmap (errno -5).                                      
portmap: server localhost not responding, timed out                             
RPC: failed to contact portmap (errno -5).                                      
lockd_up: makesock failed, error=-5                                             
portmap: server localhost not responding, timed out                             
RPC: failed to contact portmap (errno -5).  


Any suggestions?

Thanks

---

