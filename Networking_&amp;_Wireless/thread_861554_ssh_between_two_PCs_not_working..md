---
title: "ssh between two PCs not working."
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by davemar on 2008-07-16
I've got two PCs networked together, and I can quite happily ping between them. I've got their IP addresses statically set in /etc/network/interfaces, and /etc/hosts set up so their hostnames are known to each other. Let call our hostnames pc1 and pc2 for now.

If I do "ssh pc2" from pc1 it all works fine and I'm logged on.

If I do "ssh pc1" from pc2 I get:
"ssh: connect to host pc1 port 22: Connection refused"

I'm running Ubuntu 7.10 on pc1 and 8.04 on pc2.

Could it be a firewall issue on pc2 that causing this? I'm not very clued up with networking stuff and firewalls I must admit.

I've ensured that openssh-server is installed on both machines.

Cheers, Dave.

---

### Post by Iowan on 2008-07-17
**sshd** is running on pc1 (I know you said it is installed)? Both machines have common usernames?

---

