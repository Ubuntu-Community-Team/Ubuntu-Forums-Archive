---
title: "[SOLVED] nfs-common won't start"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by clarknova on 2008-10-02
Ubuntu 8.04.1 server x86_64
3 NICs

Fairly fresh install on a router, I've just added openssh-server and samba and enabled port forwarding. While installing nfs-kernel-server, nfs-common and portmap, nfs-common won't start. dmesg gives the following:
```

RPC: failed to contact local rpcbind server (errno 5).
RPC: failed to contact local rpcbind server (errno 512).

```
I've googled those errors and they appear to usually indicate that portmap is not running, but
```

$ sudo netstat -lntp | grep portmap
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      24073/portmap

```
clearly it is. I'm not running any firewall internally and I configured portmap to not run on the loopback interface. The only iptables command I've entered is
```

iptables -t nat -A POSTROUTING -s 192.168.0.0/22 -o eth0 -j MASQUERADE

```
With portmap running, why is nfs-common not able to bind it?

FYI, samba, sshd and other services running fine.

db

---

### Post by jones139 on 2008-10-02
I've never used netstat before - are you sure that what you are seeing means that portmap is running, and not that it is in the services list?  
I would have done
   ps -ef | grep portmap
to check
Whenever I install ubuntu I have to explicitly install portmap to get NFS working.
Just a thought - sorry if you have already been there!

---

### Post by clarknova on 2008-10-02
netstat won't show it if it's not running, but just to complete the picture
```

$ ps -ef | grep portmap
daemon   24073     1  0 13:04 ?        00:00:00 /sbin/portmap
david    24835 23268  0 14:40 pts/1    00:00:00 grep portmap

```

I believe portmap was installed as a dependency of nfs-kernel-server or nfs-common, but I installed it explicitly just to be sure.

db

---

### Post by jones139 on 2008-10-03
Just hoped it might have been easy....I did once have trouble with host names in /etc/hosts being wrong.  Have you seen this thread?  [http://ubuntuforums.org/showthread.php?t=629780]("http://ubuntuforums.org/showthread.php?t=629780")  It sounds similar to your problem.

---

### Post by clarknova on 2008-10-03
> **jones139 said:**
> Just hoped it might have been easy


How's this for easy? It seems to be working fine now. Not sure what I did that would have fixed it, other than reboot. Had I been working in some other OS that would have been one of the first things tried! Oh the irony. Thanks for the sympathy.

db

---

