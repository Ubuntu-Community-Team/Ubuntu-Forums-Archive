---
title: "Install NFS problems"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by dmsn on 2008-03-02
Im trying to install NFS on my server but no luck here, Someone maybe know how i can fix this ?


root@server:/etc/init.d# apt-get install nfs-kernel-server nfs-common portmap
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  nfs-common nfs-kernel-server portmap
0 upgraded, 3 newly installed, 0 to remove and 218 not upgraded.
Need to get 0B/360kB of archives.
After unpacking 987kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package portmap.
(Reading database ... 37975 files and directories currently installed.)
Unpacking portmap (from .../portmap_6.0-5_i386.deb) ...
Selecting previously deselected package nfs-common.
Unpacking nfs-common (from .../nfs-common_1%3a1.1.1-13_i386.deb) ...
Selecting previously deselected package nfs-kernel-server.
Unpacking nfs-kernel-server (from .../nfs-kernel-server_1%3a1.1.1-13_i386.deb) ...
Setting up portmap (6.0-5) ...
Setting up nfs-common (1:1.1.1-13) ...
Stopping NFS common utilities: statd.
Starting NFS common utilities: statd failed!
Setting up nfs-kernel-server (1:1.1.1-13) ...
Starting NFS common utilities: statd failed!
invoke-rc.d: initscript nfs-common, action "start" failed.
dpkg: error processing nfs-kernel-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:/etc/init.d#

---

### Post by Red.Heron on 2008-03-02
I'm having similar issues... however, mine started only recently when I was doing an update to the system. 

```

Setting up nfs-common (1:1.1.1-12ubuntu2) ...
 * Stopping NFS common utilities                                                                                                         [ OK ]
 * Starting NFS common utilities                                                                                                         [fail]

Setting up unfs3 (0.9.19+dfsg-1) ...
Starting unfs3: Cannot register service: RPC: Timed out
unable to register (NFS3_PROGRAM, NFS_V3, udp).
invoke-rc.d: initscript unfs3, action "start" failed.
dpkg: error processing unfs3 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up librrds-perl (1.2.19-1ubuntu1) ...
Setting up bindgraph (0.2a-2.1) ...
Starting DNS Statistics: bindgraph.

```

WTF??? FAIL?

Noooooooo!

(I can has nfs?)

Okay, seriously, it was working JUST fine a while ago. In fact I only rebooted 2 days ago. Firewall's intact, md5sums check, and the only changes I've made have been updates. So what gives? I'm not allowed to connect or lock, or what?

---

