---
title: "nfs server that only the remote root can access."
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by cherva on 2014-02-04
How to setup nfs server that once mounted on a remote machine should give read and write only to root and not to everyone else like it is currently doing ?
Current /etc/exports on server: /volume1/mysqldumps     192.168.XXX.XXX(rw,async,no_wdelay,no_root_squash,insecure_locks,anonuid=0,anongid=0)
Current /etc/fstab on client: 192.168.XXX.XXX:/volume1/mysqldumps /nas/mysqldumps nfs auto 0 0
Now as soon as /nas/mysqldumps mounts it gets 777 permissions.

---

### Post by SeijiSensei on 2014-02-04
Try adding "umask=077" to the client-side options like this:
```
192.168.XXX.XXX:/volume1/mysqldumps /nas/mysqldumps nfs defaults,umask=077 0 0
```
I'd also get rid of the anonuid and anongid entries in /etc/exports.  

Also make sure the mount point /nas/mysqldumps itself has only 700 permissions.

---

### Post by cherva on 2014-02-05
Based on fstab documentation umask is for non nfs mounts. For nfs it is only this: [http://unixhelp.ed.ac.uk/CGI/man-cgi?nfs+5]("http://unixhelp.ed.ac.uk/CGI/man-cgi?nfs+5") where I can't find anything about permissions. And the mount point folder is 700.

---

### Post by SeijiSensei on 2014-02-05
Then I think the permissions are based on those of the exported share itself.  Is it also 700?  

When I use no_root_squash, the share can be mounted by root, but the permissions enforced are those of the remote server.  For instance, I export /home from my server and mount it to a location under /media.  My access to those exported directories is the same on the client as it is on the server.  If I'm logged into the client with my username (the same on both machines), I can see the files on the exported share to which my username grants me permissions.  So unless the exported share is also only visible to root, I don't think you can accomplish what you want to do.

---

