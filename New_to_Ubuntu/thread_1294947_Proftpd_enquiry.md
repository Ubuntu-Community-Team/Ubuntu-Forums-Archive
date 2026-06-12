---
title: "Proftpd enquiry"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by hungryOrb on 2009-10-18
Hi all,
I've some noob questions I'm afraid..
I wanted to check which ftp servers there are installed on a machine I'm checking. Then I'd like to check which port(s) it/they are using. Then I'd like to change to port 21.. is that possible?
Which ports are available for a ftp to use?
I guess it has proftp, but I'm not sure..

Thanks for considering,

---

### Post by elvisd on 2009-10-21
aptitude search ftp package with the i letter are installed.
once identified the installed server search on forums for an how-to guide to configure it

---

### Post by martrn on 2009-10-21
Type :
```
dpkg --get-selections | grep ftp
```
to find out what ftp software is installed on your ubuntu machine.

Ports 20 and ports 21 are historically used for ftp transfers but you could use other ports that are available.

---

