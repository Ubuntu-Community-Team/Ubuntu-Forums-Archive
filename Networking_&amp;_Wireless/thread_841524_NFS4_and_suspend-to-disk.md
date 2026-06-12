---
title: "NFS4 and suspend-to-disk"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by mrarsoft on 2008-06-26
Hi,

i have two machines: one NFS4 server and a client machine. The client mounts several shares from the server including the home directories. On the client i want to use suspend-to-disk to minimize the start-up time of the client.
This scenario works fine if i suspend the client and resume the client after a short period of time (some minutes). But if i suspend the client and resume it after several hours, the client has some severe problems accessing the files on the NFS mount. The client hangs for quite some time and tries to load the files, but it doesn't succeed.
Does anyone have a clue how to get the resume working even after some time?

Thanks

---

