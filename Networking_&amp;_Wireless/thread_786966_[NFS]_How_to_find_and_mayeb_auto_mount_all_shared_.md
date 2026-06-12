---
title: "[NFS] How to find and mayeb auto mount all shared file on network ?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by Dji on 2008-05-08
Hi.
With NFS running on my server, I'm able to mount a folder on my client.
       mount sudo mount 192.168.2.103:/home/server/tmp /home/client/shared

But the trouble is that on my client I have to know the exact path. So if there are a lot of shared files on the server, it may be boring to type a long path and to type each path x).

So I'm wondering if there is a command allowing to know all folders that are shared on the server and if there is a way to mount them all at once ?

Thank you for your help ladies and guys :guitar:

---

### Post by njparton on 2008-05-09
You can add them to your fstab file so you only have to do that once.  Follow this link:
 
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/network-file-system.html)
 
(still works for 8.04).

---

