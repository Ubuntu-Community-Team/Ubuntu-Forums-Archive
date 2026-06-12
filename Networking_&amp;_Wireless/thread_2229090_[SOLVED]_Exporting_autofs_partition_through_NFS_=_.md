---
title: "[SOLVED] Exporting autofs partition through NFS = BIG problem"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by Andre_Jolivet on 2014-06-11
Hello, a little contribution to avoid the same loss of time for others ...  Foreword :  This is NOT an issue about mounting NFS directories on a client with autofs on the client side. This is about fstab mounting on a client of a NFS directory sitting on a server using autofs.   The situation :  On my home server, I have an autofs mounted LVM partition, sitting on a couple of big USB disks (quite convenient to scale the server up at will). I use autofs to mount the LVM partition because the LVM partition does not always mount correctly through fstab mount at boot (time to spin the disks). A bit of a theoritical point because the server is always "on", but ... Everything is fine up to this point ... Samba sharing works well, no problem.  The problem :  But NFS fails to export the LVM partition. mount -t nfs waits eternally (I stopped it after 10 minutes), even if I make sure the autofs mounting has happened through "ls" or something in a terminal. No error logged, everything seems allright. It looks as if NFS thought he should simply wait for the partition to mount on the server side.  The solution :  I have made a link from the LVM partition to somewhere else on the server /home. Then the link mounts perfectly and immediately on the client side. The files are seen with some lag at the first access, due to autofs time to mount the LVM directory itself (normal).  Be careful, the mount on the client behaves exactly as an autofs mount point, that is it eats everything on the mount point. No way to mount different server directories as subdirectories on the client mount point. I have had to make a different mount point for the other server directories to see them.  Final word :  This was a trial & error solution. If somebody can explain this in detail, I am interested. In particular, why is the mounted link behaving on the client as an autofs mount ? Other solutions ?  [http://ubuntuforums.org/images/icons/icon7.png](http://ubuntuforums.org/images/icons/icon7.png)

---

