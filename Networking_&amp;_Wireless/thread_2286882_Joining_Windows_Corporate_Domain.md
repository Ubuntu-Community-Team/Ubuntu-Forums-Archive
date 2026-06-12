---
title: "Joining Windows Corporate Domain"
date: 2015-07-15
forum: Networking &amp; Wireless
---

### Post by jay99 on 2015-07-15
Im having issues trying to connect Ubuntu 14.04 on a raspberry Pi 2 to a corporate Windows domain so that i'm able to search to a internal web link. 

Does anyone have a guide of how to do this as others I have tried have not been successful 

Thanks

---

### Post by Bucky Ball on 2015-07-15
Please explain in more detail what it is exactly you are trying to do. Which 'internal web link' are you trying to reach?

---

### Post by jay99 on 2015-07-15
Its a link to an intranet page on our server. We cant even search to the intranet page. 

We're trying to join Ubuntu to the domain in the hope that it will then be able to search to the intranet page

---

### Post by wyliecoyoteuk on 2015-07-15
To join a domain, you will need samba client, ldap and winbind, and it can be quite complicated, but I am not sure that is what you need.

Most likely you will be able to connect via [http://nameorIPaddressofserver/path/to/page](http://nameorIPaddressofserver/path/to/page) or [https://nameofserver/path/to/page](https://nameofserver/path/to/page)

e.g. [https://myintranetserver/owa](https://myintranetserver/owa) or [https://192.168.1.99/owa](https://192.168.1.99/owa) on my network takes you to outlook web access on our exchange server and asks for a login.

---

