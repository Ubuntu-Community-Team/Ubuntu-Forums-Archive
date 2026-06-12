---
title: "How does Autofs (direct mapping) support failover?"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Yonggang on 2008-11-26
Hi,

Recently I am trying to research Linux Autofs, but I have a problem can't be solved for a few weeks:
In auto.master, I wrote this:
```
/mnt/nfs -fstype=nfs,ro,nolook 242.82.130.13,242.220.134.211:/mnt/local
```
this is direct mapping, with duplicate servers 242.82.130.13, and 242.220.134.211. 
I know in the first time I browse the mounted file, autofs will select between the two servers. but what I want to say is, after that, if the selected server fails, autofs doesn't try to connect other servers, instead, it just retry connecting the failed server again and again. so could anybody tell me actually how to enable the failover mechanism of autofs in this case? thank you.

---

