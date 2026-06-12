---
title: "Networking Configuration (Alternate Install)"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-08-27
Hi,

I just installed Ubuntu using the Alternate Install CD. When installing, I selected the "Configure network at a later time" option during the install.

I am now having trouble getting Unison to work, where the newly installed machine is the host and my other machine (which has run Unison flawlessly in the past) is the client. The client cannot contact the server.

I have installed Unison, as well as the ssh client/host metapackage on both machines. I also have installed the Samba packages on both machines.

From the client, I can see the host only if I find it through the "Windows Shares" folder. It does NOT appear in the regular network folder.

The host cannot see the client from the host at all.

Is the error being caused by the network configuration (or lack thereof)?

All help is greatly appreciated.

Thanks,
Kurt

---

### Post by jkurtisr32 on 2010-08-28
Solved.

Followed instructions at the following link:
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

