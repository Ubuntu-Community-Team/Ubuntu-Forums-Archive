---
title: "Dovecot mail server setup"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by speedygarth on 2010-05-07
hi all i installed Linux 9.04 jaunty and everything is okay so far, i`m trying to add users onto a mail server using dovecot and i`ve been on various linux help sites but i cant find info on how to add pop3 email account users to dovecot, i also need help with setting the squid proxy service to listen on port 8080.
could someone please help!

---

### Post by Gone fishing on 2010-05-07
I haven't done this with dovecot but I have used Postfix and courier. The perfect sever guides on Howtoforge are good [http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2](http://www.howtoforge.org/perfect-server-ubuntu-9.04-ispconfig-2).

I use Webmin to configure Squid which makes it easy.

---

### Post by speedygarth on 2010-05-11
thanks i`l kep looking but what i wanted help on was the dovecot config, adding users from the email server.
do happen to know of any piece of software that can be used to monitor & filter internet usage like allocatting time for each user on the network.

---

### Post by Gone fishing on 2010-05-11
Squid can do all sorts - you can connect with LDAP for instance then give users different access etc. I can't say I know how to do this as I give different users different IP addresses then squid  gives different IP ranges different internet  access. 

In my case 192.168.1.2 - 192.168.1.240 filtered internet which isn't usable from 10.00 p.m. to 6.00 a.m. 192.168.2.2 - 192.168.2 255 unfiltered internet access.

Squidguard is a very powerful filtering tool I use. 

SARG (Squid Analysis Report Generator) very powerful report generating tool that will tell you what and where users have been and done

---

### Post by speedygarth on 2010-05-14
hey thanks for the info, maybe i really dont need dovecot if postfix can be used to manage my email server.
but what i need to know now is how do i create a mail directory to recieve the incoming mail. i think i`ll try out the courier mail.
thanks a lot.

---

