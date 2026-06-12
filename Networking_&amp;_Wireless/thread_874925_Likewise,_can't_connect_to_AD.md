---
title: "Likewise, can't connect to AD"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by jehaeberle on 2008-07-30
I have installed Likewise open. I am using the Likewise GUI to join the Windows 2003 server domain. When I try to log in using the domain name and user name the desktop will not connect to the AD. I have disconnected from the domain and rejoined the domain but still can't log in to the AD. What am I doing wrong?

---

### Post by jcbwalsh on 2008-08-12
The guide at [http://www.likewisesoftware.com/resources/user_documentation/Likewise-Open-Guide.pdf](http://www.likewisesoftware.com/resources/user_documentation/Likewise-Open-Guide.pdf) has a number of tests you can run to determine what's going wrong.

---

### Post by GigabyteMe on 2008-08-20
I had the same issue; turns out when disjoining the computer, its account was not removed from AD [I could still see it in ADUC].

after manually deleteing the account, I was successfully able to rejoin the domain.

---

