---
title: "General NFS exports question"
date: 2014-10-04
forum: Networking &amp; Wireless
---

### Post by zyberwoof on 2014-10-04
I'd like to make an export rw for one machine, and ro for the rest. I'd like to do something like this:

```
/dir 192.168.1.0/24(rw)
/dir/dir2/dir3 192.168.1.5(rw) 192.168.1.0/24(ro)
```

Essentially, I'd like to be able to make dir3 writable from only one machine on my local network, and read only from the rest.  What is the correct syntax for this?

---

### Post by TheFu on 2014-10-04
I'd have the machine hostnames resolved in order and use
/build          buildhost0[0-9].local.domain(rw)
/build          buildhost1[0-9].local.domain(ro)

Or you can check the export manpage for details.

There is an issue with the /dir export allowing everything too. Mixing rw and ro on the same storage exports is a bad idea, IMHO.
[https://access.redhat.com/solutions/454723](https://access.redhat.com/solutions/454723)

---

