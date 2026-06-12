---
title: "nfs problem"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by peterthewolf on 2008-05-17
I am trying to link two ubuntu gutsy pcs using a HOWTO I found on this forum entitled NFS Server/Client. Both pcs are running kernel 2.6.22-14-generic. On the first pc I installed all went without any problem. However when I got to the second pc I ran into a problem. The following is the terminal log and at the end you can see the problem.

peter@test-pc:~$ sudo apt-get install nfs-kernel-server nfs-common portmap
[sudo] password for peter:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk1.2 libglib1.2 libxine1-gnome libgtk1.2-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  nfs-common nfs-kernel-server portmap
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 357kB of archives.
After unpacking 1024kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  portmap nfs-common nfs-kernel-server
Install these packages without verification [y/N]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main portmap 6.0-1ubuntu1 [33.1kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main nfs-common 1:1.1.1~git-20070709-3ubuntu1 [176kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main nfs-kernel-server 1:1.1.1~git-20070709-3ubuntu1 [148kB]
Fetched 357kB in 1s (321kB/s)          
Preconfiguring packages ...
Selecting previously deselected package portmap.
(Reading database ... 117926 files and directories currently installed.)
Unpacking portmap (from .../portmap_6.0-1ubuntu1_i386.deb) ...
Selecting previously deselected package nfs-common.
Unpacking nfs-common (from .../nfs-common_1%3a1.1.1~git-20070709-3ubuntu1_i386.deb) ...
Selecting previously deselected package nfs-kernel-server.
Unpacking nfs-kernel-server (from .../nfs-kernel-server_1%3a1.1.1~git-20070709-3ubuntu1_i386.deb) ...
Setting up portmap (6.0-1ubuntu1) ...
 * Starting portmap daemon...                                            [ OK ] 

Setting up nfs-common (1:1.1.1~git-20070709-3ubuntu1) ...

Creating config file /etc/idmapd.conf with new version

Creating config file /etc/default/nfs-common with new version
 * Starting NFS common utilities                                         [ OK ] 

Setting up nfs-kernel-server (1:1.1.1~git-20070709-3ubuntu1) ...
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/net/sunrpc/sunrpc.ko': No such file or directory
WARNING: Error inserting lockd (/lib/modules/2.6.22-14-generic/kernel/fs/lockd/lockd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting nfsd (/lib/modules/2.6.22-14-generic/kernel/fs/nfsd/nfsd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
 * Not starting NFS kernel daemon: no support in current kernel.

peter@test-pc:~$ uname
Linux
peter@test-pc:~$ uname -r
2.6.22-14-generic
 

How do I fix this
Thanks in anticipation.

---

