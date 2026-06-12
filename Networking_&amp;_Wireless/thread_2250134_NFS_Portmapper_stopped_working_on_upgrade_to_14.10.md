---
title: "NFS Portmapper stopped working on upgrade to 14.10"
date: 2014-10-26
forum: Networking &amp; Wireless
---

### Post by zon14 on 2014-10-26
I have a backup file server I use to sync files between it and a couple laptops when I'm home.  On the server I upgraded to 14.10 from 14.04, but when trying to mount -t nfs server:/home/export /home/server/export times out on the client.

When I looked at the server, the /etc/export file is still there, and untouched.

But when I tried /etc/rc0.d/K01nfs-kernel-server start, I get:

*Starting NFS kernal daemon:
*Not starting: Portmapper is not running.

So...great.  Looks like I need to start the portmapper somehow.  But how?

---

### Post by zon14 on 2014-11-17
Anyone?

---

### Post by SeijiSensei on 2014-11-17
Try using "sudo service nfs-kernel-server  start" to start the service.  Any better?

I just looked at my version of that package on my 14.04 machine with "dpkg -s nfs-kernel-server".  It doesn't list portmap as a dependency:
```

Version: 1:1.2.8-6ubuntu1.1
Depends: libblkid1 (>= 2.16), libc6 (>= 2.15), libcap2 (>= 2.10), libsqlite3-0 (>= 3.5.9), libtirpc1, libwrap0 (>= 7.6-4~), nfs-common (= 1:1.2.8-6ubuntu1.1), ucf, lsb-base (>= 1.3-9ubuntu3)

```
It also starts right up after complaining about subtree_check.

---

### Post by steeldriver on 2014-11-17
Isn't the "portmapper" actually rpcbind? which is a dependency of nfs-common I think

---

### Post by SeijiSensei on 2014-11-18
You're right.  zon14, did you have nfs-common installed?  It should have happened automatically as a dependency of nfs-kernel-server.

The dependencies for nfs-common are rather extensive:
```

Package: nfs-common
Version: 1:1.2.8-6ubuntu1.1
Depends: libc6 (>= 2.15), libcap2 (>= 2.10), libcomerr2 (>= 1.01), libdevmapper1.02.1 (>= 2:1.02.20), 
libevent-2.0-5 (>= 2.0.10-stable), libgssglue1, libkeyutils1, libkrb5-3 (>= 1.6.dfsg.2), libmount1 (>= 2.19.1), 
libnfsidmap2, libtirpc1, libwrap0 (>= 7.6-4~), sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), 
**rpcbind **(>= 0.2.0-6ubuntu1), adduser, ucf, lsb-base (>= 1.3-9ubuntu3), 
initscripts (>= 2.88dsf-13.10ubuntu1), mountall (>= 2.41)

```

---

### Post by zon14 on 2014-12-25
I did have nfs-common installed during 14.04.  Though now some interesting update must have solved it, for it's working again.  Don't ask me how or why.

---

### Post by zon14 on 2014-12-27
Or so I thought.  It started doing it again.  What I did was reinstall rpcbind, and that seems to have done it finally.

---

