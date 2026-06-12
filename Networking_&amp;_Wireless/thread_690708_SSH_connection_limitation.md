---
title: "SSH connection limitation"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by wiseguyxp on 2008-02-07
On my Ubuntu 7.10 Server machine, I would like to limit SSH connections to one active connection per user.  I attempted to do this in the /etc/security/limits.conf file with the "maxlogins" options set to 1.  The problem with this is that users are unable to access their SSH accounts when they get disconnected from their wireless Internet (which is sketchy) because I believe the connection is staying logged in.  The SSH connection is just used for forwarding ports.  I also intend to implement using key authentication instead of password authentication fairly soon, so if there's a different way to do this for key auth, I would like to go ahead and try that instead.

---

### Post by wiseguyxp on 2008-02-07
bump?

---

