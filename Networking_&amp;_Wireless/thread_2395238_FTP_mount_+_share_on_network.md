---
title: "FTP mount + share on network"
date: 2018-06-28
forum: Networking &amp; Wireless
---

### Post by teckthekid on 2018-06-28
[COLOR=#1C1C1C][FONT=&quot]Hello,
[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]

[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&quot]I do not know if it is possible but I need to mount a ftp address which is easy to do, but can I share mounted location on network with ftp connection being active?
[/FONT][/COLOR]

---

### Post by TheFu on 2018-06-28
FTP?  That protocol should have died in 1996. There are many better, more secure, easier to access, methods for files.  Is FTP the only offering from the other side?

I don't know of any way to share a FUSE mount to others, but ftpfs might be useful.   I use sshfs all the time, but it is also a FUSE file system, so limited to the user who made the connection.  FUSE file systems will be slow but that should already be expected for access going over the internet anyways.

If you have control over the remote box, getting them to setup read-only NFSv4 shares would be better.

---

### Post by teckthekid on 2018-06-30
Yeah  sorry I am using sshfs.

Thing is I need a constant connection on it and to be able to share mount across different pc's

---

### Post by TheFu on 2018-06-30
> **teckthekid said:**
> Yeah  sorry I am using sshfs.

Thing is I need a constant connection on it and to be able to share mount across different pc's

You lost me.  Is it FTP or sshfs? Actually, it doesn't matter. the remote system controls the permissions.

Have you considered straight replication with periodic updates?  **rsync** is good at that.
Then you can share the files on your local network using NFS.

---

