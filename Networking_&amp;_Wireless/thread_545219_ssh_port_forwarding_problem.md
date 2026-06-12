---
title: "ssh port forwarding problem"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by John Harrington on 2007-09-07
I have installed openssh server, I can log in on localhost, and port scan of localhost shows port 22 open.  I'm behind a wireless home router, and have forwarded port 22, but I get no response when trying to log in using my internet IP address.  Port scan of the internet address shows port 22 closed.  I tried setting up ssh to listen on port 8888 in case my ISP blocks port 22 (although port 22 is not on the list of ports they say are blocked), but again, port 8888 was open on localhost but not on the router, even though I set it up to forward it.

I've got other ports forwarded (5800 and 5900 for VNC), and they work fine.  There's no difference that I can see in the router port forwarding settings for the VNC ports and the ssh ports except for the port numbers.  Can anybody suggest what I'm doing wrong?  Thanks.

---

### Post by noob12 on 2007-09-07
Have you tried connecting from a point outside your router's local network?  On many routers using the external address and forwarded port from within your local network won't work, but it works fine from outside.

---

### Post by newlinux on 2007-09-07
I've had this same problem with ssh. Router set to a port, sshd set to listen to that port. Can't connect from outside my firewall. If I setup port 22 to forward to ssh it works. If I ssh to the alternate port from inside the firewall (using the internal IP of course) it works so I know ssh is listening to the alternative port. Something is happening with the forwarding.

Interested in answers as well...

---

### Post by noob12 on 2007-09-09
John Harrington:  If you are still having the problem, can you post the output of these for diagnostics.  I'll watch the thread for one more day, then you'll need to PM me to get my attention.
```

netstat -tnl

route -n

```

---

### Post by John Harrington on 2007-09-09
Noob 12, thanks very much for responding and waiting to help me. However, at least for me it's now working fine.    Port 22 shows up on port scan from my own computer over the exernal IP address, and I can login through SSH using that address.    I can't think of anything I did that could have fixed it except to cycle the router off and on and shutdown and restart the computer.  In the past, I think changes in router settings have taken effect as soon as I apply them.  Anyway, the problem has resolved itself.

---

### Post by noob12 on 2007-09-09
Great to hear.

---

