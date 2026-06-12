---
title: "workstation setup for any user"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by rickrack on 2011-03-24
As a new administrator for Ubuntu, I can think of ways of writing custom programs for doing this, but it seems as though there may be a utility or a simple way of doing this.

I would like to know if I can do the following:
Can I create ubuntu workstations that any user can log into and query the ubuntu server for their permissions and only their user files stored on the server?
Then can I have that user/group permissions setup the user/group gui for running certain programs at the workstation and other programs at the server?

Thank you all for any help!

---

### Post by Zzl1xndd on 2011-03-24
It sounds like you are attempting to set up directory service. If this is the case can you tell us what kind of server you will be using for it?

(Eg: Active Directory, E-Directory, OpenLDAP, 389 directory, etc)

---

### Post by rickrack on 2011-03-24
both server and workstation are Ubuntu 10.04LTS

---

### Post by Zzl1xndd on 2011-03-24
Does this sound like what you are looking for?

> Lightweight Directory Access Protocol (LDAP) is a network protocol for accessing and manipulating information stored in a directory.

Services built on the LDAP protocol are used to serve a wide range of information. The protocol is well-suited to serving information that must be highly available and accessible, but does not change frequently. A common application is the storage of user account information such as usernames, logins, IDs, email addresses, and (in some configurations) password.

Storing such information in an LDAP directory makes it available to any host on the network. With the proper configuration, a user can move between computers, logging using the same set of credentials. This unified login process is commonly know as Single Sign On (SSO). It is often used to provide unified access to shared resources such as file systems and printers, and seamlessly migrate a user's desktop environment between computers. 

---

