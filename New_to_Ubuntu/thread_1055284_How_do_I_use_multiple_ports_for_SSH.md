---
title: "How do I use multiple ports for SSH?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by TMcKSmith on 2009-01-30
I use Ubuntu Server (Intrepid).
I'd like to use ports 22 (which is working fine now - of course), but also ports 1494 and 443.  How do I do this?
I already forwarded the ports on my router.  What is the next step?  
Thanks.

---

### Post by bodhi.zazen on 2009-01-30
Nice walk through here :

[http://fixunix.com/ssh/364505-running-multiple-sshd-instances-one-server.html](http://fixunix.com/ssh/364505-running-multiple-sshd-instances-one-server.html)

---

### Post by Hospadar on 2009-01-30
Probably the easiest way is to just forward all those ports on your router to port 22.  I don't see any reason your router shouldn't let you forward multiple external ports to the same internal port.

Otherwise, there is probably some mysitc iptables command to do it or maybe netstat.  Googling the two might turn up some useful results.

I don't know if it's possible to make sshd (the ssh server process) listen to multiple ports, but I'm sure you can internally redirect those ports, or maybe start multiple copies of sshd listening to different ports

---

### Post by TMcKSmith on 2009-01-30
Figured it out -

I just added 

Port 1494
Port 443

under "Port 22" in the sshd_config file

---

