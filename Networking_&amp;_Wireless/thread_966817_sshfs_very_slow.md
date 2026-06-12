---
title: "sshfs very slow"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by ds0111 on 2008-11-01
Hi! I am having trouble with sshfs on ubuntu 8.04 (installed via package manager): 

sshfs is very slow, ls of a directory containing maybe 20 small files takes several seconds, or displaying a (small, just a few bytes) file also takes several seconds. 

Doing the same dircetly on to the remote machine via ssh is almost instant, and the connection is fast enough to run simple X applications via ssh, so something is amiss, I guess.

Manipulating the cache_timeout_... options didn't seem to help. (Hitting tab to complete filenames works fast though, so some caching seems to be done).

Thanks in advance!

David

---

