---
title: "Folder permissions for BIND9"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Richie4236 on 2008-10-30
Hi,

I recently started working with Ubuntu server as a way of delivering some basic network services to our remote offices without the need to put a Windows box in place.  Things like DHCP, DNS and some basic file sharing.

I got DHCP to work without a problem, but I can't make BIND work.  I want it to act as a slave to our central AD/DNS server.  All seems to be set up correctly.  I'm pretty sure the problem is down to directory permissions.  The syslog shows an error when trying to create the temp for the zone transfer.

> Oct 30 13:33:11 pegasus named[4589]: dumping master file: /etc/bind/tmp-kleLcfNzMC: open: permission denied

I read on a couple of forums that I can get around this with chroot, however I don't feel comfortable enough with Linux yet to understand what I'm doing.  What I really need is a simple way to make this work.

Thanks in advnace.

---

### Post by Yarbo on 2008-10-30
Bind has been giving me a hard time lately as well, I also have a permission error.  Except my permission error is in relation to BIND not being able to access named.pid.

---

### Post by davidshere on 2008-11-03
> **Richie4236 said:**
> I'm pretty sure the problem is down to directory permissions.  The syslog shows an error when trying to create the temp for the zone transfer.

I've found this tutorial to be extremely useful when setting up an Ubuntu server:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I had a similar problem with Bind -- wouldn't start because of file permissions.  I got a slightly different error message:

```
Nov  1 21:55:23 raptor named[8798]: starting BIND 9.5.0-P2
Nov  1 21:55:23 raptor named[8798]: found 2 CPUs, using 2 worker threads
Nov  1 21:55:23 raptor named[8798]: loading configuration from '/etc/bind/named.conf'
Nov  1 21:55:23 raptor named[8798]: none:0: open: /etc/bind/named.conf: permission denied
Nov  1 21:55:23 raptor named[8798]: loading configuration: permission denied
Nov  1 21:55:23 raptor named[8798]: exiting (due to fatal error)
Nov  1 21:55:23 raptor kernel: [21864.484292] type=1503 audit(1225590923.010:10): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=0 name="/var/lib/named/etc/bind/named.conf" pid=8799 profile="/usr/sbin/named"

```

This was quite frustrating because I'd get this error even if the permissions on /etc/bind/named.conf were 777.  What solved the problem for me was removing apparmor.  (Which is in the above tutorial)

---

### Post by davidshere on 2008-11-03
> **Richie4236 said:**
> I'm pretty sure the problem is down to directory permissions.  The syslog shows an error when trying to create the temp for the zone transfer.

I did some experimenting and it appears that bind has to have execute permissions to the zones directory.

---

