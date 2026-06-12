---
title: "Problem with nfs on Ubuntu 16.04"
date: 2016-04-22
forum: Networking &amp; Wireless
---

### Post by fasolens on 2016-04-22
Hi there,
I installed Ubuntu Server 16.04 and I try to set up nfs server.
When I ```
apt install nfs-kernel-server
``` it returns:
```
Creating config file /etc/idmapd.conf with new version

Creating config file /etc/default/nfs-common with new version
Adding system user `statd' (UID 107) ...
Adding new user `statd' (UID 107) with group `nogroup' ...
Not creating home directory `/var/lib/nfs'.
nfs-utils.service is a disabled or a static unit, not starting it.
Setting up nfs-kernel-server (1:1.2.8-9ubuntu12) ...
A dependency job for nfs-server.service failed. See 'journalctl -xe' for details.
nfs-server.service couldn't start.


Creating config file /etc/exports with new version


Creating config file /etc/default/nfs-kernel-server with new version
A dependency job for nfs-server.service failed. See 'journalctl -xe' for details.
invoke-rc.d: initscript nfs-kernel-server, action "start" failed.
dpkg: error processing package nfs-kernel-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (229-4ubuntu4) ...
Errors were encountered while processing:
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

In  journalctl -xe there is:```

-- 
-- Unit proc-fs-nfsd.mount has failed.
-- 
-- The result is failed.
kwi 22 08:11:58 nfs systemd[1]: Dependency failed for NFS Mount Daemon.
-- Subject: Unit nfs-mountd.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit nfs-mountd.service has failed.
-- 
-- The result is dependency.
kwi 22 08:11:58 nfs systemd[1]: Dependency failed for NFS server and services.
-- Subject: Unit nfs-server.service has failed
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- Unit nfs-server.service has failed.
-- 
-- The result is dependency.
kwi 22 08:11:58 nfs systemd[1]: nfs-server.service: Job nfs-server.service/start failed with result 'dependency'.
kwi 22 08:11:58 nfs systemd[1]: nfs-mountd.service: Job nfs-mountd.service/start failed with result 'dependency'.
kwi 22 08:11:58 nfs systemd[1]: proc-fs-nfsd.mount: Unit entered failed state.
kwi 22 08:12:58 nfs systemd-journald[37]: Forwarding to syslog missed 12 messages.
-- Subject: One or more messages could not be forwarded to syslog
-- Defined-By: systemd
-- Support: http://lists.freedesktop.org/mailman/listinfo/systemd-devel
-- 
-- One or more messages could not be forwarded to the syslog service
-- running side-by-side with journald. This usually indicates that the
-- syslog implementation has not been able to keep up with the speed of
-- messages queued.
kwi 22 08:17:01 nfs CRON[1866]: pam_unix(cron:session): session opened for user root by (uid=0)
kwi 22 08:17:01 nfs CRON[1867]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
kwi 22 08:17:01 nfs CRON[1866]: pam_unix(cron:session): session closed for user root

```

Is there something new in 16.04 I should set up?

I have to add that this is inside LXD container.

---

### Post by alonso7 on 2016-04-23
Same problem here.

---

### Post by fasolens on 2016-04-27
I managed with this by installing older version of packages.
First install nfs-common
[https://packages.debian.org/sid/nfs-common](https://packages.debian.org/sid/nfs-common)
next
[https://packages.debian.org/sid/nfs-kernel-server](https://packages.debian.org/sid/nfs-kernel-server)

Regards

---

