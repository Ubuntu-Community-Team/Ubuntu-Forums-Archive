---
title: "keyserver error"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by k33bz on 2009-09-11
I have tried several times now, and still get the same response when I am trying to get a key.
```
work@mobile:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

When I try to reach keyserver.ubuntu.com it hangs and says it can not connect. However when I ping it I get:
```
work@mobile:~$ ping keyserver.ubuntu.com -c 4
PING keyserver.ubuntu.com (91.189.94.173) 56(84) bytes of data.
64 bytes from esperanza.canonical.com (91.189.94.173): icmp_seq=1 ttl=45 time=142 ms
64 bytes from esperanza.canonical.com (91.189.94.173): icmp_seq=2 ttl=45 time=141 ms
64 bytes from esperanza.canonical.com (91.189.94.173): icmp_seq=3 ttl=45 time=141 ms
64 bytes from esperanza.canonical.com (91.189.94.173): icmp_seq=4 ttl=45 time=140 ms

--- keyserver.ubuntu.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 140.728/141.646/142.511/0.642 ms

```

Please help I need to get this key.

Thanks.

After the 8th try it finally went through.

---

