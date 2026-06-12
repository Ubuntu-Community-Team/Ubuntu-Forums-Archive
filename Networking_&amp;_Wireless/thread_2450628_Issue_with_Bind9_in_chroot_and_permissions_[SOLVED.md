---
title: "Issue with Bind9 in chroot and permissions [SOLVED]"
date: 2020-09-17
forum: Networking &amp; Wireless
---

### Post by hanji866 on 2020-09-17
Hello all!

New to ubuntu (migrating from gentoo). I have a server started and trying to install bind9 in a chroot environment. I have the chroot created, but getting the dreaded 'loading configuration from '/etc/bind/named.conf''

I'm running into a wall, because the obvious if the bind user has access is true.

kernel: audit: type=1400 audit(1600391424.664:39): apparmor="DENIED" operation="open" profile="/usr/sbin/named" 

```
name="/chroot/dns/etc/bind/named.conf" pid=5096 comm="named" requested_mask="r" denied_mask="r" fsuid=113 ouid=113
```

So requested_mask of read, is getting the denied_mask of read. Odd.

My chroot is here:

/chroot/dns/

```
ls -al /chroot/
total 12
drwxr-xr-x  3 root root 4096 Sep 18 00:33 .
drwxr-xr-x 20 root root 4096 Sep 18 00:33 ..
drwxr-xr-x  6 bind bind 4096 Sep 18 00:33 dns
```

For the sake of debugging, I made sure this is owned by bind:bind and is 755. Once we get this working, I would like to make this root:root 750.

named.conf is in /chroot/dns/etc/bind/named.conf

Here are some permissions...

```
/chroot/dns# ls -al
total 24
drwxr-xr-x 6 bind bind 4096 Sep 18 00:33 .
drwxr-xr-x 3 root root 4096 Sep 18 00:33 ..
drwxr-xr-x 2 bind bind 4096 Sep 18 00:36 dev
drwxr-xr-x 3 bind bind 4096 Sep 18 00:31 etc
drwxr-xr-x 2 bind bind 4096 Sep 18 00:33 run
drwxr-xr-x 6 bind bind 4096 Sep 18 00:31 var

/chroot/dns/etc# ls -al
total 16
drwxr-xr-x 3 bind bind 4096 Sep 18 00:31 .
drwxr-xr-x 6 bind bind 4096 Sep 18 00:33 ..
drwxr-xr-x 2 bind bind 4096 Sep 18 00:49 bind

/chroot/dns/etc/bind# ls -al
total 60
drwxr-xr-x 2 bind bind  4096 Sep 18 00:49 .
drwxr-xr-x 3 bind bind  4096 Sep 18 00:31 ..
-rw-r----- 1 bind bind  2389 Sep 18 00:31 bind.keys
-rw-r--r-- 1 bind bind 44582 Sep 18 00:49 named.conf
-rw------- 1 bind bind    77 Sep 18 00:31 rndc.key
```

So bind is the owner, all the way down to named.conf. I've even dropped to a unpriv user and was able to view named.conf. So not sure what is up.

Here is my start up options:

```
cat /etc/default/named
#
# run resolvconf?
RESOLVCONF=no

# startup options for the server
OPTIONS="-u bind -t /chroot/dns -c /etc/bind/named.conf"
```

Not sure what's up. Any ideas?

Thanks!
hanji

---

### Post by hanji866 on 2020-09-17
I just figured it out. Just solved it (subject edited).

I had to update /etc/apparmor.d/usr.sbin.named and restart apparmor. Bind9 started up fine.

Super newb over here.

h

---

