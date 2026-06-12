---
title: "Using sshfs"
date: 2018-10-06
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2018-10-06
I am trying to use sshfs to remotely mount a share.  It returns with the error, "read: Connection reset by peer."  I turned off iptables on the server hosting the storage, and I added input/output rules on the server that is requesting the storage mount.  In watching the packets, the last thing I see on the requesting server is that there is a response from the storage server, from port microsoft-ds, but nothing back after that.  Is there something else that I am missing here?

---

### Post by TheFu on 2018-10-06
Does ssh work between the client and the server?  Thats the only port and authentication used by sshfs.

---

### Post by SeijiSensei on 2018-10-07
Try testing with "ssh -vv hostname" which increases the debugging of the client.  Also look at /var/log/syslog on the server and see if it throws any errors.

---

