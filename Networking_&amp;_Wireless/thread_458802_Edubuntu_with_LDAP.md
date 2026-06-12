---
title: "Edubuntu with LDAP"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by nroussi on 2007-05-30
Hi I have recently setup an edubuntu server with a few thin clients (no HD). The clients are increasing in the numbers of around 200 and that would mean that I would need to use multiple servers (maybe 3 or 4) to manage efficiently the number of clients. I wanted to use a fifth server as an LDAP server so that I could have all the user accounts in this central server.

This is my plan but since I have no idea about LDAP I thought I ask for a few opinions. And for a step further, is it possible on this LDAP server to get the usernames and passords for the thin clients from a mySQL database?

Appreciate any comment.

---

### Post by skarphedin on 2007-05-30
> **nroussi said:**
> Hi I have recently setup an edubuntu server with a few thin clients (no HD). The clients are increasing in the numbers of around 200 and that would mean that I would need to use multiple servers (maybe 3 or 4) to manage efficiently the number of clients. I wanted to use a fifth server as an LDAP server so that I could have all the user accounts in this central server.

This is my plan but since I have no idea about LDAP I thought I ask for a few opinions. And for a step further, is it possible on this LDAP server to get the usernames and passords for the thin clients from a mySQL database?

Appreciate any comment.

I manage close to 200 Ubuntu clients, 10 of them LTSP, about 100 laptops and the rest desktops. In the largest site with about 70 of them I use LDAP. 

LDAP is a protocol to acess a X.500 directory so usernames / passwords are alredy stored in some sort of database (optimized for reads).  You can fetch usernames and passwords initially from Mysql, but you have to maintain a separate copy in the directory accessed by LDAP.

I manage the information stored in the directory with various python and shellscripts. I have for instance created a Python script to change the passwords of users. I also have a script to generate usernames and passwords for new accounts based on the users name and output a LDIF file (format used for exports / inports of the directory) that can be imported in the directory.
A graphical LDAP browser like GQ is also nice to use if you want to make a few changes.

It is a good idea to buy a book like LDAP system administration by Carter (O'Reilly). 

You can probably find well integrated directory solutions for Linux as well if you want a simple solution.

---

