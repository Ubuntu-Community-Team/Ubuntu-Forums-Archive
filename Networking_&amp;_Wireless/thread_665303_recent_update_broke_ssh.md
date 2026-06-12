---
title: "recent update broke ssh?"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by flabbah on 2008-01-12
On 2008-01-10, openssh-server was updated to 1:4.6p1-5ubuntu0.1 through the Ubuntu auto-update mechanism. Since then, I have not been able to connect to my machine using SSH. My /var/log/auth says:

Jan 12 03:06:24 xxxx sshd[5613]: Server listening on :: port 22.
Jan 12 03:06:24 xxxx sshd[5613]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.

It does not matter which port I use. I did the obvious and restarted the service / machine. This did not occur before the update. Does anyone have any ideas?

The relevant stuff in my sshd_config is:

Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0

When I try to connect to this machine, I get the 'Connection Timed Out" error from the ssh client.

Thanks a lot.

---

### Post by amo-ej1 on 2008-01-12
Have you tried to take a look with netstat -anp to see what is actually keeping the port busy ?

---

### Post by nnikcm on 2008-01-22
I am having the same problem.  I checked `netstat -anp` as suggested, but nothing was using port 22.

---

### Post by nnikcm on 2008-01-22
I think I found the problem, update your sshd_config file to and comment out:

ListenAddress ::

and uncomment:

ListenAddress 0.0.0.0

then restart sshd.

It has something to do with ssh binding to ipv6 addresses by default.

---

