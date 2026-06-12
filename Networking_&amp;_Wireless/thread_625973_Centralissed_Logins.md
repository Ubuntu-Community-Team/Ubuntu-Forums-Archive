---
title: "Centralissed Logins"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by sg_robinson on 2007-11-28
Hi there, 

Ive been looking around on the itnernet for a way of having centralized logins on a server. I.E i have ONE server for everything (network shares, users, Ftp and apache). I know having all one one server is probably not the best idea but id just like to try it all out! Sooo...

Anyone have any suggestions of a method of storing all usersnames on the server (along with passwords)   then using the clients to retrive the username and passwords from the server? After this i would also like to be able to store the users files on the server instead of having each users files on each client!

I was using webmin and adding users to each computer but came accross a flaw.. How would users change passwords with this method!

Any help would be greatly appreciated :)

Thanks,
Fet

:guitar:

---

### Post by scorp123 on 2007-11-28
> **sg_robinson said:**
>  Anyone have any suggestions of a method of storing all usersnames on the server (along with passwords)   then using the clients to retrive the username and passwords from the server?  You may want to look into **OpenLDAP**. There are some good books and plenty of "how to's" and tutorials out there.   
[http://en.wikipedia.org/wiki/Openldap](http://en.wikipedia.org/wiki/Openldap)
[http://www.openldap.org/](http://www.openldap.org/)

> **sg_robinson said:**
>  After this i would also like to be able to store the users files on the server instead of having each users files on each client!  This could be done via **NFS** (network file system).   [http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29](http://en.wikipedia.org/wiki/Network_File_System_%28protocol%29)

---

### Post by scorp123 on 2007-11-29
I just ran across this and I guess this is what you want:

"Building an LDAP Server on Linux, Part 1"
[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3088441](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3088441)

Quote from the text there: > 
... _What LDAP Can Do_

In a nutshell, LDAP provides central management of access, authentication, and authorization. It's easily customizable and can:

    * Centralize user and group management
    * Centralize information stores
    * Set security and access control
...

---

