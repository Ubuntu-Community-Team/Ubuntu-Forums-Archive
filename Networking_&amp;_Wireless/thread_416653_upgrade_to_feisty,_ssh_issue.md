---
title: "upgrade to feisty, ssh issue?"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by greatshape on 2007-04-21
Hi,

Just upgraded from edgy to feisty, everything went great thoug got something strange here.
When I try to ssh to a server in my network (ssh root@192.168.x.x) it takes about 10 seconds to get a reply from the server. (it takes about 10sec before I can enter the password) 
But, when I try to connect tot he same server from the outside (ssh [email]root@public.ip[/email]), it works fluently. 
Then i get the password request in a second. 
I played around with ~/.ssh/known_hosts , but it didn't solve the problem.  
Anyone has a solution for this? Waiting 10sec for a local connection is frustrating :-) 

Many tnx
Yves

---

### Post by pete on 2007-04-22
I installed Feisty from scratch yesterday and am getting exactly the same behavior, resulting in the same frustration.  I'll reply here if I figure anything out.

---

### Post by pete on 2007-04-22
Check [this thread]("http://ubuntuforums.org/showthread.php?t=377212").  I followed the tips there and my ssh is back to normal.

---

### Post by greatshape on 2007-04-22
> **pete said:**
> Check [this thread]("http://ubuntuforums.org/showthread.php?t=377212").  I followed the tips there and my ssh is back to normal.

Tnx Pete, commenting out the GSSAPI* lines solved the problem for me too. 

Kind regards,
Yves:)

---

