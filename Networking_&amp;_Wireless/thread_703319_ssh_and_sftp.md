---
title: "ssh and sftp"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by moxy1 on 2008-02-21
This may be a really basic question, but I've searched a lot and cannot find an answer to it. I've somehow lost ssh access to my server and cannot figure out how to restore it. When I issue:

sudo /etc/init.d/ssh restart

it responds with:

/etc/ssh/sshd_config line 152: Subsystem 'sftp' already defined.     [failed]

What exactly does this mean and how can I fix it?

---

### Post by SpaceTeddy on 2008-02-21
it means that you are trying to load the subsystem "sftp" twice... 
enter your sshd_config (found in /etc/ssh/sshd_config) and comment out line 152 (as it states in the error).

that ought to fix it...

---

### Post by moxy1 on 2008-02-21
I can't believe that's all it was. That worked like a charm. Thanks a ton :)

---

