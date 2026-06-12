---
title: "IP loads router issue"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by frup on 2006-11-25
Hi have what I think could be a security problem with my router, when entering my IP from a remote computer the routers admin page prompting for username and password shows up.

Whats the best way to change this? I'm thinking of making just my apache load instead... is it as simple as editing the apache.conf file or what ever it is to allow http connections or will I have to dabble in port forwarding etc or is it likely my router is a **** and I should get a new one?

Can anyone tell me what the best method to approach this issue is and point me to the right sources of anything else I might need to set up?

---

### Post by frup on 2006-11-25
bump :)

---

### Post by scxtt on 2006-11-25
that's really strange, generally that's only possible if you have "Remote Management" enabled to use port 8080 (i.e. [http://1.2.3.4:8080](http://1.2.3.4:8080) [that's a fake IP since i don't know yours] would prompt you for your admin login) ... seems to be a router issue only - maybe try resetting it, cause that can't be default behavior ...

---

### Post by frup on 2006-11-26
Well it came like that by default... I just had a very thourough look through the admin page and found one thing under misc configuration called http server access... i made that restricted... now i just hope in future i can still access this over lan.

Would this stop apache from being able to work over http?

I understand i might have to do a simple port forward anyway and the edit of apache.conf (which i haven't really looked in to too much) Would denying http through the router full on restrict all access (note it says 403 forbiden under /doc/index.htm 

How can i get access to the router to change the index.htm?

---

