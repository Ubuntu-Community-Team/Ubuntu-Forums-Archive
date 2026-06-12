---
title: "Cannot SSH in from outside my LAN"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by guitarMan666 on 2008-05-30
This problem has been plaguing me for quite some time.  I cannot SSH into my computer from outside my network.  The server side computer is running Ubuntu Studio Hardy (kernel 2.6.24-17-rt) and the client side is a QEMU virtual machine running Damn Small Linux 4.3 (kernel 2.4.31).  This configuration works fine within the LAN, I can access any program I wish including GUI programs, however, connecting from the outside the traffic does not come in, returning a connection refused error.

My configuration listens on 443 (a port unblocked to outbound traffic at the college) which is forwarded by my router (Westell 327w if it makes a difference, Verizon is my provider).  A Standard Port Security scan from [http://www-ss.com](http://www-ss.com) reveals that the port is indeed open.  

If you need more information than that to solve this just ask and i'll post it too.
As always, thank you all in advance for your time.

---

### Post by bluefrog on 2008-05-30
if you try to get out of your network then come back to your network, you will not succeed.

You will be able to enter your LAN if you are physically outside your LAN.

---

### Post by rampageoberon on 2008-05-30
You need inbound connections to be allowed ot your ssh port (22). Most colleges/organisations don't allow inbound connections.

---

### Post by guitarMan666 on 2008-06-12
> **rampageoberon said:**
> You need inbound connections to be allowed ot your ssh port (22). Most colleges/organisations don't allow inbound connections.
Port 22 is not the issue.  I was told previously on this forum (a few months ago) to use either Port 80 or better yet Port 443 (the latter of which I use in my setup to great success from anywhere but school), in order to visit and exchange information with websites using those Ports, wouldn't they HAVE to allow incoming traffic on those ports?

I could not find that old post again to reference, hence the new thread.

---

### Post by kevdog on 2008-06-12
So your server at home is listening on port 443?

Can you confirm this with 
sudo netstat -an | grep ssh

Is port 443 on your router forwarded to your computer?

---

### Post by guitarMan666 on 2008-06-13
Netstat outputs: 
unix  2      [ ACC ]     STREAM     LISTENING     15184    /tmp/keyring-Ind74c/ssh

Yes, the port is forwarded.  The connection works anywhere but school, I'm beginning to think the issue is on their end.

---

