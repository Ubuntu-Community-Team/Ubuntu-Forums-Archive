---
title: "NFS mount gives &quot;mount.nfs: Protocol not supported&quot;"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by per-stromgren on 2013-10-20
Old machine, runnung on Ubuntu 13.04 can mount NFS server just fine.

New machine, running 13.10, using identical /etc/fstab (or command line mount) gives the result "mount.nfs: Protocol not supported"

mount -v gives on both machine:

```
per@linus:/$ sudo mount -v -t nfs lagret:/home /mnt/lagret
mount.nfs: timeout set for Sun Oct 20 20:29:33 2013
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.201,clientaddr=192.168.1.127'
mount.nfs: mount(2): No such file or directory
mount.nfs: trying text-based options 'addr=192.168.1.201'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.1.201 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.1.201 prog 100005 vers 3 prot UDP port 37918
mount.nfs: portmap query retrying: RPC: Program/version mismatch
mount.nfs: prog 100005, trying vers=3, prot=6
mount.nfs: trying 192.168.1.201 prog 100005 vers 3 prot TCP port 43816
mount.nfs: portmap query failed: RPC: Program/version mismatch

```

Old machine, that works, continues to mount anyway. New does not.

Any hints?

Per.

---

### Post by SeijiSensei on 2013-10-20
Did you install the **nfs-common** package?  That's a requirement to use the computer as an NFS client.  It does not ship with Ubuntu by default.

---

### Post by per-stromgren on 2013-10-20
Yes, I did.

---

### Post by SeijiSensei on 2013-10-20
> mount.nfs: mount(2): No such file or directory

That's a rather weird error.  I presume you are exporting /home in lagret's /etc/exports, and /mnt/lagret exists?  

What are the mount options in /etc/exports?  Do they include "insecure" which lets the client choose a source port > 1023?  Also in the "text-based options" line it seems to be trying to use NFSv4, but the rest of the text talks about using NFSv3.  Also are you trying to force a TCP connection?

Can we see both the entry in /etc/exports and in /etc/fstab?  What does syslog report on the server?

---

### Post by per-stromgren on 2013-10-21
Thanks for the reply. I don't have the answers right here, but will check and get back here in about 6 hours.

No, I don't know what I'm doing, really .... :-) 

Per.

---

### Post by per-stromgren on 2013-10-21
Success, kind of!

I was very confused about if I was using NFS4 or not, so I inserted an "fsid=0,no_subtree_check" into my /etc/exports file, and changed the mount command to "<server>:/" on the client side. Now it does mount without error messages. 

I still have a severe performance problem; it is a lot slower than my old configuration on the old client machine.

Hacking on....

---

### Post by SeijiSensei on 2013-10-22
> **per-stromgren said:**
> I still have a severe performance problem; it is a lot slower than my old configuration on the old client machine.

Add "async" to the list of options in the server's /etc/exports.  That exposes you to possible data loss if the server were to crash during a transfer, but if the server is reliable it's not much of a threat.  Mine is attached to uninterrupted power supply, so I have about twenty minutes after a power outage before it goes down.  Plus I use APC equipment with the apcupsd Linux daemon.  It monitors the UPS and executes a graceful shutdown when the battery is running low.

---

### Post by r-senior on 2013-11-22
I'm also seeing this error after upgrading from 13.04 to 13.10. NFS had been working fine.

I haven't got to the bottom of it but I think it is because the client is trying to use Kerberos authentication. From my syslog:

```

Nov 23 00:52:18 wharfe kernel: [ 4846.896061] RPC: AUTH_GSS upcall timed out.
Nov 23 00:52:18 wharfe kernel: [ 4846.896061] Please check user daemon is running.

```

I get these lines every time I try to mount. The mount comes back with the same messages as OP. I have tried:

```
sudo mount -t nfs4 -osec=sys server:/export /mnt/mount
```

But that doesn't help.

[https://ask.fedoraproject.org/question/30612/nfs-gss-problems-on-f19/](https://ask.fedoraproject.org/question/30612/nfs-gss-problems-on-f19/)
[http://osdir.com/ml/linux.nfsv4/2006-10/msg00048.html](http://osdir.com/ml/linux.nfsv4/2006-10/msg00048.html)
[http://ubuntuforums.org/showthread.php?t=2182975&p=12836460#post12836460](http://ubuntuforums.org/showthread.php?t=2182975&p=12836460#post12836460)

---

### Post by r-senior on 2013-11-23
OK, I have it working again. Basically, all I did was update my old exports to follow the pattern given in here under "NFSv4 without Kerberos":

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

---

