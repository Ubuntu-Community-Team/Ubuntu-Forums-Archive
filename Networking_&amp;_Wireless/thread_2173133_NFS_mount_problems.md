---
title: "NFS mount problems"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by slowmo on 2013-09-08
Hi

I have set up an NFS server and an NFS client but I am unable to mount the server shares from the client. 

There is no DNS set up but both have the same /etc/hosts file and the 'user' has the same id on both machines. 

Using 'showmount -e' from the client gives the following results

> sudo showmount -e serverip
Export list for serverip: 
/var/nfs		serverip 
/home/user		serverip 

This is my attempt to mount the NFS share

> sudo mount -v serveripaddress:/home/user /home/user

mount: no type was given - I'll assume nfs because of the colon
mount.nfs: timeout set for Sun Sep  8 11:04:52 2013
mount.nfs: trying text-based options 'vers=4,addr=serveripaddress,clientaddr=clientipaddress'
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting serveripaddress:/home/user

However **'showmount -a'** and **'showmount -d'** do not produce any results. 

If I run 'host clientip' from the server I get the following result

> host clientip

Host clientipreversed.in-addr.arpa. not found: 3(NXDOMAIN)

In addition to this I ran **'ps aux | grep rpc'** on the server: 

> root       982  0.0  0.0      0     0 ?        S    08:05   0:00 [rpciod/0] 
root       983  0.0  0.0      0     0 ?        S    08:05   0:00 [rpciod/1] 
statd      988  0.0  0.0   1988   788 ?        Ss   08:05   0:00 rpc.statd -L 
root      1009  0.0  0.0   2392   560 ?        Ss   08:05   0:00 rpc.idmapd 
root      1419  0.0  0.0   2228   824 ?        Ss   08:06   0:00 /usr/sbin/rpc.mountd --manage-gids 
1000      4604  0.0  0.0   3352   848 pts/0    S+   11:41   0:00 grep rpc

and the client

> root       711  0.0  0.0  19200  1060 ?        Ss   10:56   0:00 rpcbind -w
root       957  0.0  0.0      0     0 ?        S<   10:56   0:00 [rpciod]
statd      983  0.0  0.0  21504  1356 ?        Ss   10:56   0:00 rpc.statd -L
root      1006  0.0  0.0  25540   676 ?        Ss   10:56   0:00 rpc.idmapd
1000     16757  0.0  0.0   9392   916 pts/1    S+   11:31   0:00 grep --color=auto rpc

Is anybody able to tell me what the problem is and how to resolve it? Thanks for any help.

---

### Post by TheFu on 2013-09-08
I dunno, but doesn't nfsv4 require a manual exchange of keys between the client and server before anything works?
Googled "nfs v4 howto ubuntu" and the top 3 results were all to specific help.ubuntu.com pages. The first link had instructions differnt from what you've described above.

---

### Post by SeijiSensei on 2013-09-08
You cannot mount an NFS share as the root user unless no_root_squash is an option in the server's /etc/exports.  Without that option, root is mapped to the anonymous user.  See "[man exports](http://linux.die.net/man/5/exports)" for details.

---

### Post by slowmo on 2013-09-09
Thanks for the responses. I'll cjheck my /etc/exports file and also compare the NFS V4 instructions to what I did. When I've done that I'll post again how I got on.

---

### Post by slowmo on 2013-09-15
I have looked into this more thoroughly and the problem for me lay with the /etc/exports file. 

I had made the assumption that as I was exporting it was necessary to indicate the server address in the exports file, like so: 

> /home/user	**serveripaddress**(rw,sync,no_root_squash,no_subtree_check)

However what I needed to do was to indicate what ipaddresses were allowed to access the server, like so:

> /home/user	**clientipaddress**(rw,sync,no_root_squash,no_subtree_check)

I actually used an IP address range to test it but I presume that it is fine to specify a single client IP address?

Once again thanks for the help.

---

