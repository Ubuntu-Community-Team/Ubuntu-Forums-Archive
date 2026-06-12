---
title: "Error using ssh-copy-id"
date: 2020-07-06
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2020-07-06
I'm attempting to set up ssh keys for root on my servers to allow remote backups without permission problems.

I've generated the keys but when I go to copy them to the other servers I get the following error:

```
~# ssh-copy-id root@hamlet
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/root/.ssh/id_rsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
**no such identity: /root/.ssh/hamlet_id_rsa.pub: No such file or directory**
root@hamlet's password:
```
I don't know where that error is coming form and I don't think it's right.

---

### Post by rsteinmetz70112 on 2020-07-06
I found it. I had set up a config file that referenced that file.

---

