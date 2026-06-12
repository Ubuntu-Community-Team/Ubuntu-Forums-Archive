---
title: "[SOLVED] SSH VPN fails to open"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by jimv on 2008-05-27
I'm trying to follow these instructions:

[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

And when I run this command on my laptop with the IP of my home SSH server:
```

sudo ssh -w 0:0 1.2.3.4
```

I get connected to the SSH server, but get this error message:

```
Tunnel device open failed.
Could not request tunnel forwarding.
```

Any ideas?

EDIT:

LoL, problem solved and I feel dumb.  I wasn't typing in sudo.

---

### Post by rcd412 on 2009-02-27
did you ever figure this out? I have a vanilla debian lenny guy that keeps giving tunnel device open failed when i ssh out.

---

### Post by rcd412 on 2009-02-27
well i just noticed that you commented saying you needed sudo... I get tunnel device open failed without any forwarding. From what i know i shouldn't need sudo to just plain ssh.

---

