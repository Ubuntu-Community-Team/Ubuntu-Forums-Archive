---
title: "MOTD not showing when using PKI to ssh my server"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by truse on 2008-11-02
Hi

When i first started logging in to my ubuntu 8.10 server via. SSH, i got some pretty cool output showing system load, temperature, memory usage, processes running and so on.

But, when i configured sshd_config to use public key authentication (so i don't have to type inn a password), i dont get the MOTD anymore. The only thing i see now is "Last login: <date> <time> ip.. and so on"

I don't see any changes in /etc/ssh/sshd_config that could made this disappear.

Can someone please tell me how to fix this?
Thanks in advance.

---

### Post by karloskar on 2009-03-25
I have exactly the same problem. Occured for the first time yesterday on a new Intrepid Server install.
If it's a bug then we should probably file a bug report. Does anyone know if this is expected behaviour or if we're missing something here?

---

