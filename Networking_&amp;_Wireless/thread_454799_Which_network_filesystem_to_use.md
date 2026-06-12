---
title: "Which network filesystem to use?"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by jmillikin on 2007-05-25
I'd like to create a network share hosted by a server and connected to by several clients (all UNIX-based). From what I understand NFS is the default for this sort of thing, but I've heard it 1) causes the system to hang if a mount goes down and 2) has poor locking support. The Linux kernel has support for something called "Coda", but I can't find any Coda-related packages in the repositories. Lastly, there's something called OpenAFS in universe, but the kernel support for it is marked "Experimental" and claims to be read-only.

I'd prefer to avoid Samba, because of file size limits, permission support, and the proprietary nature of the SMB/CIFS protocol - it seems dangerous to rely on reverse-engineered code for something as basic as a filesystem.

---

### Post by ruy_lopez on 2007-05-26
From my own experience, the more recent version of NFS (NFSv4) is pretty robust. Its easy to set up, and doesn't mangle permissions like Samba does.

There's a good HOWTO here:

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

The last time I tried, though, the rpc.gssapi support was pretty non-functioning, so I'd avoid the bit about kerberos, and just set it up straight.

---

