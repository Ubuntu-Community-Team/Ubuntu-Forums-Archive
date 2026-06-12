---
title: "Add a user to samba"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by mr.propre on 2008-01-04
Here is the problem:
I work with samba to share files between my Linux Laptop and my Vista Desktop.
I also take my laptop to my girlfriends place and sometimes she needs a file on my laptop or I need a file of hers. The only solution until now, was that I use her computer to log her in into my samba account on my laptop, with my password. Though I trust my GF, I only trust myself when it comes to passwords, so I always need to enter the password.

Now I would like to add a samba login to my laptop so that she can log herself in. When you google for it you find allot of tutorials, but non of them are really clear.

Can somebody help me? Thanks in advance.

---

### Post by Predator[23rd] on 2008-01-04
Adding a user to Samba
1° creating linux user: **sudo adduser *myGF***
2° creating SAMBA user: **smbpasswd -a *myGF***

should be enough ...

---

### Post by mr.propre on 2008-01-05
Is there a way to do it without making a Linux user account for my GF, I'm the only one who is using the laptop.

---

### Post by mr.propre on 2008-02-10
Sorry for the bump, its been a while.
If I add a system user, is there an option to allow him to connect to a separate network map.
But don't allow him to log-in on the machine?

---

