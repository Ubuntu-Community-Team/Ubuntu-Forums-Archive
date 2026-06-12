---
title: "Strange issue with Samba"
date: 2017-05-30
forum: Networking &amp; Wireless
---

### Post by username2758 on 2017-05-30
I'm running Ubuntu 16.04 LTS and probably after upgrading Samba it messed up with configuration files. The only workaround I found is to "sudo service nmbd restart", but I am not sure what's wrong and how to fix this.

The symptoms are the server can't be seen by other computers on network (smbtree), and when I "sudo service smbd status" for example, it gives me the following message:
> Warning: samba.service changed on disk. Run 'systemctl daemon-reload' to reload samba.service
Loaded: masked (/dev/null; bad)
Active: inactive (dead)

What is wrong with my settings and how to fix this issue?

---

### Post by SeijiSensei on 2017-05-30
16.04 uses systemd rather than the traditional SysV init methods.  Start by reading "man systemctl" for information on the new commands Ubuntu uses to start and stop daemon processes.  The "service" command is deprecated.

---

### Post by username2758 on 2017-05-30
Yes but the problem is not the commands, but with Samba not starting up correctly. I always have to manually restart nmbd service via "sudo service nbmd restart" to get my shares visible on the network. Any ideas on why and how to fix this?

---

