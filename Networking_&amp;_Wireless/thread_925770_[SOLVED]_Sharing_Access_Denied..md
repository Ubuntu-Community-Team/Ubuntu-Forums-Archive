---
title: "[SOLVED] Sharing: Access Denied."
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by zx6r1033 on 2008-09-21
I am finally getting around to trying to set up a share network with all of the computers in my house. The only problem is, Ubuntu won't let me. If I right-click on the folder I want to share, then select "Sharing Options", it gives me the box I need. Then when I check on "Share This Folder" and click "Create Share", it returns this message:

> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


... Yet another time my own computer tells me I can't do something I want to do. 

How do I get around this?

I tried searching for the answer, but everything I read says it simply works. No one else has ever had this problem?

---

### Post by darco on 2008-09-21
Open up User and groups, under  User Privleges, make sure the share files w/local network is checked...then log out and log in....
good luck

darco

---

### Post by zx6r1033 on 2008-09-21
I checked there.. it was checked. Still didn't work. 

I ended up in System>Administration>Users And Groups>username>Properties>Advanced  and changed my Main Group to "Root" in order to get it to work. 

In any event, I guess the problem is solved now.  Thanks.

---

