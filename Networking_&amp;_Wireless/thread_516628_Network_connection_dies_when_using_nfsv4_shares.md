---
title: "Network connection dies when using nfsv4 shares"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by RaZoR1394 on 2007-08-03
Hello.

I'm having problems with NFS v4 shares located on a server. I followed the guide in the documentation, [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) . There is another one here [https://help.ubuntu.com/7.04/server/C/network-file-system.html](https://help.ubuntu.com/7.04/server/C/network-file-system.html) . I think this is nfs v3 or?

The problem is that the connection dies on the client when for ex copying large files from and to the nfs share or from the client to the nfs share alternatively when unpacking a files remotely with the nfs share. What works is ssh'ing inside the server and copying/moving/unpacking there.

My /etc/exports on the server:

> 
/export       192.168.1.0/24(ro,fsid=0,insecure,no_subtree_check,async)
/export/storage 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)


My client's /etc/fstab:

> 
192.168.1.104:/ /mnt            nfs4    proto=tcp,port=2049     0       0


Thanks for the help.

---

