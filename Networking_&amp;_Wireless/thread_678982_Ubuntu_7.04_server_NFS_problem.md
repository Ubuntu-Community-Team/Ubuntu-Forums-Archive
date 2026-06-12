---
title: "Ubuntu 7.04 server NFS problem"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by lehjoz on 2008-01-26
Hello,

I have just installed the nfs server, and got the following problem:

When I restart the nfs-kernel-server, it seems working properly, however in the syslog it adds this entry:
...nfssvc: writing fds to kernel failed: errno 0 (Success)
In addition It is not possible to mount the shared directories, the client get the following error message: special device hostname/shared_directory does not exist

Does anyone know how to fix this problem?

thanx in advance: lehjoz

---

### Post by MrHippocampus on 2008-01-26
I'm having exactly the same problem, it was working fine until I installed an update (i think it was for the kernel), and then it stopped working. Haven't had time to try and find out why yet or try previous kernels but a quick look on google seems to show other people having the same problem.

---

