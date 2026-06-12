---
title: "LDAP failing to bind against AD server on domain"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by plasmarox on 2014-05-29
Hi all

I'm trying to join my freshly built virtual ubuntu machine up to my Windows domain as a domain controller using Samba. I'm running the command:

```
samba-tool domain join tim.local DC -U tim@tim.local --realm=tim.local
```

but I'm getting

```

root@tim-callisto:~# samba-tool domain join tim.local DC -U tim@tim.local --realm=tim.local
Finding a writeable DC for domain 'tim.local'
Found DC tim-dc1.tim.local
Password for [tim@tim.local]:
Failed to bind - LDAP client internal error: NT_STATUS_INVALID_PARAMETER
Failed to connect to 'ldap://tim-dc1.tim.local' with backend 'ldap': (null)
ERROR(ldb): uncaught exception - None
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/domain.py", line 552, in run
    machinepass=machinepass, use_ntvfs=use_ntvfs, dns_backend=dns_backend)
  File "/usr/lib/python2.7/dist-packages/samba/join.py", line 1150, in join_DC
    machinepass, use_ntvfs, dns_backend, promote_existing)
  File "/usr/lib/python2.7/dist-packages/samba/join.py", line 81, in __init__
    credentials=ctx.creds, lp=ctx.lp)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 56, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 114, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 71, in connect
    options=options)

```

i've therefore come to the conclusion that LDAP is unable to bind (after a google)

I've tried an anonynous ldapsearch (after a google) ```

ldapsearch -h tim.local -b'dc=tim,dc=local' -x# extended LDIF
#
# LDAPv3
# base <dc=tim,dc=local> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#


# search result
search: 2
result: 32 No such object


# numResponses: 1
root@tim-callisto:~# 



```

But this seems suspect >.<

My ubuntu box is running 14.04 lts and my server is running Windows Server 2008 R2 - it's running ADDS, DNS and DHCP

On the ubuntu box, primary DNS server is set to the server and i can successfully ping the domain

```
root@tim-callisto:~# ping tim.local
PING tim.local (192.168.1.99) 56(84) bytes of data.
64 bytes from 192.168.1.99: icmp_seq=1 ttl=128 time=1.04 ms
64 bytes from 192.168.1.99: icmp_seq=2 ttl=128 time=0.841 ms
64 bytes from 192.168.1.99: icmp_seq=3 ttl=128 time=0.540 ms
64 bytes from 192.168.1.99: icmp_seq=4 ttl=128 time=0.702 ms

```


Any ideas so far? :(

---

