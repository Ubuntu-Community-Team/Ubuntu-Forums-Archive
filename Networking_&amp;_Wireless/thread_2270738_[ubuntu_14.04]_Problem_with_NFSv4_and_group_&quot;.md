---
title: "[ubuntu 14.04] Problem with NFSv4 and group &quot;nogroup&quot;"
date: 2015-03-25
forum: Networking &amp; Wireless
---

### Post by mtemp on 2015-03-25
Hallo,

I have a problem resolving the group "nogroup" on multiple nfsv4-krb5 shares.

I'm running an ubuntu14.4 in a university network with krb5 and a nfsv4-netapp-filer (where I have no access and no documentation...)
Everything works except the translation of the group "nogroup". It only shows the gid 4294967294 instead of "nogroup". The translation of "nobody" and hundreds of users and "normal" groups however **DOES **work! 


The interesting part is that on our ubuntu12.04 and ubuntu10.04 machines  (with the same configuration) the group "nogroup" is properly translated  and mapped to (the local?) gid 65534. The only (known)  difference between the configuration of our ubuntu12.04 and 14.04 pool  is that the ubuntu14.04 machines have a fqdn and the ubuntu12.02 do not.

Of course the "NEED_IDMAPD=yes" option is set and our idmapd.conf seems to be correct and running:

```
[General]

Verbosity = 10
Pipefs-Directory = /run/rpc_pipefs
Domain = not.the.same.domain.as.the.fqdn.of.the.clients
[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
```

There are no suspicious entries in the logfiles. I have no idea how to debug is problem. Can you help me?

Best regards,
Michael

---

### Post by bab1 on 2015-03-25
> **mtemp said:**
> Hallo,

I have a problem resolving the group "nogroup" on multiple nfsv4-krb5 shares.

I'm running an ubuntu14.4 in a university network with krb5 and a nfsv4-netapp-filer (where I have no access and no documentation...)
Everything works except the translation of the group "nogroup". It only shows the gid 4294967294 instead of "nogroup". The translation of "nobody" and hundreds of users and "normal" groups however **DOES **work! 


The interesting part is that on our ubuntu12.04 and ubuntu10.04 machines  (with the same configuration) the group "nogroup" is properly translated  and mapped to (the local?) gid 65534. The only (known)  difference between the configuration of our ubuntu12.04 and 14.04 pool  is that the ubuntu14.04 machines have a fqdn and the ubuntu12.02 do not.

Of course the "NEED_IDMAPD=yes" option is set and our idmapd.conf seems to be correct and running:

```
[General]

Verbosity = 10
Pipefs-Directory = /run/rpc_pipefs
Domain = not.the.same.domain.as.the.fqdn.of.the.clients
[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
```

There are no suspicious entries in the logfiles. I have no idea how to debug is problem. Can you help me?

Best regards,
Michael

I would start [here]("http://blather.michaelwlucas.com/archives/796") and [here]("http://ubuntuforums.org/showthread.php?t=1651504").

It turns out the gid of 4294967294  is well known.  See what I got from a simple Google search of *gid 4294967294* [here]("https://www.google.com/search?client=ubuntu&channel=fs&q=gid+4294967294&ie=utf-8&oe=utf-8").  Some of the solutions are to use NFS v3.  To me that is unacceptable, but that is my preference.  I have always matched the UID/GID's across the network so I don't have this problem, but I understand that you might not have complete control of your environment.

---

### Post by mtemp on 2015-03-27
Hi
thanks for your response.

Of course I've googled that a lot and I do understand that gid 4294967294 is (like 65535) -2/-1 if considered as a signed int. Unfortunately most people have the problem that everything is owned by 4294967294/nobody/nogroup instead of the right user/group. So enabling "NEED_IDMAPD=yes" solves their problem.

However my problem is different. Here everything EXPECT nogroup works.

We are using nfs v3 where it is possible. Unfortunately there is a centralised /home for all members of our university and we are forced to use nfs4v. I have no control over that.

---

### Post by mtemp on 2015-04-07
So, one "solution" would be to add a group and an user, let's call them nfsnobody:x:4294967294:4294967294:/nonexistent:/usr/sbin/nologin and nfsnogroup:x:4294967294 and change the nobody-User accordingly in /etc/idmapd.conf. Is that a good idea?

---

