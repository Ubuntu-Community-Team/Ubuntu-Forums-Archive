---
title: "Mounting SMB shares through gateway"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by shcodip on 2007-04-21
So I recently purchased a 2TB terrastation. I love it so far. One problem though, I can't figure out how to mount the samba shares remotely. I have configured my router to forward ports 445 and 139 (both TCP) to the box however when accessing the gateway via smbmount I get timeouts on those ports as though they are not being forwarded properly. Are there any other considerations that I have missed.

~$ sudo mount -t smbfs -o username=<username>,password=<password> //<gatewayip>/share /media/test
timeout connecting to <gatewayip>:445
timeout connecting to <gatewayip>:139
Error connecting to <gatewayip> (Operation already in progress)
5428: Connection to <gatewayip> failed
SMB connection failed

When I access the machine directly (bypassing the router) I can mount the particular share fine...
~$ sudo smbclient //192.168.0.6/share -u<username>
Password:

---

