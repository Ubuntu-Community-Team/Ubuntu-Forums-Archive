---
title: "LDAP Planning"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by th3 mant1s on 2009-04-03
Hi Community,

I am preparing to deploy LDAP for the first time. Heres the situation:

Goal: provide a single sign on for 3 client machines and the server itself. A user should be able to have access for his/her files, mail and be able to change their password. 

Servers: Two boxes one acting as a master server and one acting as a slave.

Clients: All Four boxes (technically acting as servers)


Network Layout:

Box A = Master LDAP Server [LDAP: Client / Server]
Box B = Slave LDAP Server [LDAP: Client / Server]
Box C = DNS Server [LDAP Client]
Box D = DNS Slave [LDAP Client]


Questions for the community:

What LDAP Modules will I need? What are the best strategies to take on this task? Any good walk-throughs or Tutorials? How can I integrate a secure connection between the four boxes (SSL or other encryption)? 

Thank you!

-J

---

### Post by iBurger on 2009-04-07
Hi,

Welcome to the community. This forum is more targeted towards new desktop users. As a prof, please consider posting this question in the network forum. or read these topics;

[http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=Swiftfox%3Aen-US%3Aofficial&hs=tpZ&num=50&q=site%3A+ubuntuforums.org+ldap&as_qdr=y&btnG=Search](http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=Swiftfox%3Aen-US%3Aofficial&hs=tpZ&num=50&q=site%3A+ubuntuforums.org+ldap&as_qdr=y&btnG=Search)

good luck, and cool that you are here.

---

