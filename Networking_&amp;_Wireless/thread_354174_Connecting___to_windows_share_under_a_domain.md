---
title: "Connecting   to windows share under a domain"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by Biochem on 2007-02-05
The server at my university are under M$ domain but not my laptop. Actually the server is a desktop in the lab, so I have access to it but not at an admin level

 Using windows I can access shared folder by typing "\\server\share", I'm ask for my username and pasword and all I have to type is "Domain/Username" and my password and it work

With Kubuntu 6.10 I try to connect with Konkeror to my server  "smb://Server/share" and I'm ask for my Username and password. then that's where it get fuzzy. Just typing my username and password doesn't work since I need to specify the domain. But I don't know where or how to enter this information. And since I change building often I need something easily changeable so that it doesn't  interfere in other network.

Now Linux is considered an unsafe OS by the M$CE IT staff, so support is extremely limited. :roll:

---

### Post by koenn on 2007-02-05
did you try  using something of the form
```
DOMAIN\username
```
or 
```
user@domain
```
the second form is newer and resquires the domain name to be "fully qualified", like mycompany.com or mydepartment.mycompany.us or mydomain.local or something. 

Same as with windows, no ? the domain name is part of the user name, as the user is defined within the domain. Doesn't that work ?

---

### Post by Biochem on 2007-02-06
Thank you for your help koenn,

I did try entering the Domain and username separated with /,\ , @ , - , # , $ , &  in both order to no avail. That is why I'm confused. 

Is it possible that it is AMD64 specific?

---

### Post by koenn on 2007-02-07
no, it's stricktly software and protocols. 
strange.

---

### Post by ltsix on 2008-03-04
Check this link out little over half way down it explains samba + domain [http://handsonhowto.com/2007/what-is-samba/](http://handsonhowto.com/2007/what-is-samba/) 

Regards,
-Andy

---

