---
title: "NFS - high cpu usage and network traffic under edgy eft caused by getattr"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by paneq on 2007-02-13
Two weeks ago i was using Ubuntu DD under my client and Debian Testing
under my server and everything was fine until I decided recently to
switch both systems to Edgy Eft. What is the problem now ?

Note: Server exports /home directory and clients imports it.

When I log into console everything is still ok, but after I log into X
session (gnome) cpu usage comes to about 80% and there is high network
traffic between server and client (what can be easly seen on router
diods). I had no idea what could cause it so I captured the traffic
using ethereal (Wireshark). Almost whole network traffic was caused by
client's getattr request and nfs server answers to those request.
Every request has the same file id and hash so it means that the
client wants all the time to know the attributes of the same file. I
do not have any idea how to check what file it is, or which process
causes it and why it happens.

nfsstat shows that 99% of requests is getattr.
top and htop shows only cpu usage of user space. NFS works in kernel.

Does anyone know what's wrong?
I hope you can help me.
Have a good day, people :-)

---

### Post by crazee64 on 2007-09-20
Did you find a cause for this? 
I am also experiencing this problem, although not the high CPU aspect, just the multiple GETATTR calls for the same id. I am not certain but I think it may have started after I installed nfs-common.

---

