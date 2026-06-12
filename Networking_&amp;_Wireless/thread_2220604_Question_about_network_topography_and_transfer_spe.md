---
title: "Question about network topography and transfer speeds"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2014-04-28
Say you have two servers: Server 1 and Server 2

In addition you have one workstation, through which you access both via SSH.

Will there be any difference in transfer speed between:

1) Opening SFTP connections to both servers in a GUI file browswer to initiate a bulk transfer of files from one server to another, and

2) using a tool like scp to directly transfer files from one machine to another.

I guess I'm asking if the workstation playing middle-man will have an impact, of if a direct connection is still being made.

---

### Post by tgalati4 on 2014-04-28
I would suspect that the gui sftp transfer would be slighly slower because the gui display has to be refreshed to the workstation and that sends traffic to the workstation that interferes with the file transfer between the two servers.  If you have a high-quality router with a sufficiently fast backend, you may not notice the difference.  

One test is worth a thousand opinions.

---

