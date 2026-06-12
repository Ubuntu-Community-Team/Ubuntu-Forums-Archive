---
title: "Slow NFS mounts on diskless clients"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by skarphedin on 2007-05-30
I'm experimenting with a diskless Ubuntu 7.04 setup in order to ease administration of 30 Ubuntu desktops. I have the following setup:

Server 1 (Tor):
- Runs DHCP, DNS, CUPS
- Provides NFS exported homedirectories

Server 2 (Sigyn):
- TFTP
- NFS exported root filesystems
- NFS exported /usr

Client 1 (vus-dl1).

I have a separate root filesystem for each diskless client. All clients mounts a shared  /usr ro .
During boot I get a long delay (more than 1 minute) when the diskless clients mounts /usr. According to Ubuntu NFS mounting of /usr fails during boot, but /usr is mounted anyway when the client finally  is ready. If I try to mount /usr manually from the same client after it has completed booting it mounts in a second without any errors.

rpcinfo -p Client1:

 program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100021    1   tcp   1641  nlockmgr
    100021    3   tcp   1641  nlockmgr
    100021    4   tcp   1641  nlockmgr
    100024    1   udp   1024  status
    100024    1   tcp   3078  status

rpcinfo -p Server1:

 program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100021    1   udp  32771  nlockmgr
    100021    3   udp  32771  nlockmgr
    100021    4   udp  32771  nlockmgr
    100021    1   tcp  32775  nlockmgr
    100021    3   tcp  32775  nlockmgr
    100021    4   tcp  32775  nlockmgr
    100005    1   udp    669  mountd
    100005    1   tcp    672  mountd
    100005    2   udp    669  mountd
    100005    2   tcp    672  mountd
    100005    3   udp    669  mountd
    100005    3   tcp    672  mountd
    100024    1   udp    709  status
    100024    1   tcp    712  status

rpcinfo -p Server2:

 program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32768  nlockmgr
    100021    3   udp  32768  nlockmgr
    100021    4   udp  32768  nlockmgr
    100021    1   tcp  47477  nlockmgr
    100021    3   tcp  47477  nlockmgr
    100021    4   tcp  47477  nlockmgr
    100005    1   udp    865  mountd
    100005    1   tcp    868  mountd
    100005    2   udp    865  mountd
    100005    2   tcp    868  mountd
    100005    3   udp    865  mountd
    100005    3   tcp    868  mountd
    100024    1   udp  32774  status
    100024    1   tcp  45561  status

In /var/log/syslog of the diskless client I get these NFS messages (192.168.1.35 is Server2)

May 30 11:14:23 ubuntu kernel: [ 1554.122081] nfs: server 192.168.1.35 not responding, still trying
May 30 11:14:42 ubuntu kernel: [ 1573.674691] nfs: server 192.168.1.35 not responding, still trying
May 30 11:15:10 ubuntu kernel: [ 1601.688644] nfs: server 192.168.1.35 not responding, still trying
May 30 11:15:12 ubuntu kernel: [ 1603.567169] nfs: server 192.168.1.35 not responding, still trying
May 30 11:15:56 ubuntu kernel: [ 1647.798987] nfs: server 192.168.1.35 OK
May 30 11:15:56 ubuntu kernel: [ 1647.800002] nfs: server 192.168.1.35 OK
May 30 11:15:56 ubuntu kernel: [ 1647.800822] nfs: server 192.168.1.35 OK
May 30 11:15:56 ubuntu kernel: [ 1647.800979] nfs: server 192.168.1.35 OK


Everything seems to be OK exept for this NFS  problem. Do you have any suggestions? 

Best regards,

Erling

---

### Post by skarphedin on 2007-06-01
I still have this problem with 7.04. I have tested a diskless setup with Debian 4.0 and do not experience such mount delays so it seems like something is wrong with the setup on 7.04. Will try Ubuntu Dapper as well to test if I have the same problems with that version.

---

