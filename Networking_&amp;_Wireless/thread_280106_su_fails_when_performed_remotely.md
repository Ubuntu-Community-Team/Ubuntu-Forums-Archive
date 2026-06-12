---
title: "su fails when performed remotely"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by M_F_H on 2006-10-19
On Ubuntu 6.06, I can su to root when I'm at the computer, but when I ssh to the same computer then su, I'm told that my password failed.  This happens when I ssh from both a remote host as well as when I 'ssh M_F_H@localhost'.  

I suspect that PAM is configured to deny su'ing from ssh-generated tty's, but would appreciate any assistance...

P.S. In case it is not clear, the root password has been set on the box that I'm ssh'ing into.

---

