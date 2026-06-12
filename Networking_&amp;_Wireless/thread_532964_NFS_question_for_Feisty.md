---
title: "NFS question for Feisty"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by ljs_1969 on 2007-08-23
Hi NFS experts,

I'm new to NFS. I have a question about testing my NFS setting.
Can I install the NFS server and client in one computer? It's easy for my test. 
Now I got an error message, ''mount to NFS server '140.92.62.220' failed: server is down".
Does anybody can help me out?

Thanks,

Richard Li

---

### Post by ScorpKing on 2007-08-27
i'm not sure if both the server and client will work when running on the same machine, i've never tried it. you'll have to install nfs-kernel-server on the server and configure /etc/exports . restart the nfs-kernel-server after changing any options. on the client side make sure you have portmap installed. if it's not installed the mount seems to take forever. i added this on my box to fstab to make the directory automount at startup. "www.server.com:/home/user /mnt/mountpoint  nfs rw,hard,intr 0 0" check the logs for errors. nfs works for me without any problems. play around with the options in the /etc/exports to add some sort of security to the server. good luck

---

