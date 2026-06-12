---
title: "sharing"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by aidanh on 2007-01-31
ok so i want to setup file sharin between my ubuntu deskto computer and my windows desktop computer..

how would i go about setting it all up???

eaasy instructions plz!!!


Aidanh

---

### Post by Stochastic on 2007-02-01
I haven't done this myself but I know that Samba is the program you need to look into.  Do a search, there must be easy setup instructions somewhere.

---

### Post by aidanh on 2007-02-01
found how to setup samba server/or install it but its says this:

aidan@ubuntu:~$ sudo apt-get install samba
Password:
Sorry, try again.
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Stochastic on 2007-02-01
do you have any other package managers running (add/remove programs or synaptic package managaer)?  If not, try rebooting and doing the same code.

---

