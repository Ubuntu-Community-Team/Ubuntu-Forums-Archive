---
title: "Evolution mail crashing on startup, Ubuntu 9.04"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by leonardo_neo on 2009-05-23
Hello,

I am using Ubuntu 9.04. I left my computer on sleeping mode for 7-8 hrs. After restarting, I found evolution mail is not there. When I try to launch evolution mail, it is not able to do so, and simply crashing. Restarting to computer also doesn't solve the problem. Any idea whats going on? 

Thanks in anticipation :)

---

### Post by mprince on 2009-05-24
You might want to check out this bug report. I sounds like what you are experiencing. 

[https://bugs.edge.launchpad.net/ubuntu/+source/samba/+bug/363791](https://bugs.edge.launchpad.net/ubuntu/+source/samba/+bug/363791)

---

### Post by leonardo_neo on 2009-05-24
Thanks a lot mprince for giving your time to answer my question.

Anyway, I have solved the problem. I had manually upgraded the version of Open office 3.1. After installation I was not able to run the Open office database. So I searched in the forum, and found a command to solve the issue. After running that command, database was fine with everything. Even evolution had no problem, until yesterday it stopped launching.

So I removed the openoffice.org-evolution package from synaptic package manager, and now evolution is working again. Database is not launching again, but it is OK for me, as evolution is more essential for me.

If someone has installed OO 3.1, and experience the similar problem, then they can try this temporary fix.

Thanks to all.

---

