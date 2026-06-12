---
title: "Which server/client method for sharing network drives?"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by theseeker on 2007-11-13
Hi companeros! 

Well, could you point me out which method I should use to share my data (disk mounts as well as /home) between my laptop and my desktop, both running ubuntu gutsy? I have currently  implemented the nfs client/server, my desktop being the server for start. But, I don't know how to manage permissions in my mounted drives on the desktop in order to use them as user (not root) on my laptop. 

Anyway, the goal is to share everything containing data (disk mounts and /home) both ways, with security, since the laptop is on wireless. Good tutorials are much appreciated (but I haven't found any complete ones yet). Is the ssh method more flexible for the purpose? Please give me some good advice!

Thanx a lot for any help!!! (and sorry for my flawed english, it's not my native tongue!)

:)

---

### Post by Yoooder on 2007-11-13
Here's a tutorial on setting up a basic NFS share:

[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing]("http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing")

As for security, it allows read/write by any client within the network.  So if your network (including your wireless) is secure then it should suffice.

If security on your network isn't so good, then I would say that SCP (SSH Copy) would be a good option--however it may be a bit more cumbersome.

---

