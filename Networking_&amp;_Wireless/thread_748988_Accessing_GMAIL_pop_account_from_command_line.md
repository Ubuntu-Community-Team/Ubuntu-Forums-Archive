---
title: "Accessing GMAIL pop account from command line"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by debjit_bis08 on 2008-04-08
I was trying to learn about POP n tried to access my gmail account using

*openssl s_client -connect pop.gmail.com:995*

i did get connected but was unable to access any, it dint even show i hav pending email

+OK Gpop ready for requests from 220.225.244.123 m27pf6833346wag.0
user [email]myusername@gmail.com[/email]
+OK send PASS
pass ********
+OK Welcome.
stat
+OK 0 0
list
+OK 0 messages (0 bytes)
.
noop
+OK
rset
+OK
list
+OK 0 messages (0 bytes)
.
uidl
+OK
.
quit
+OK Farewell.
read:errno=0

wat am i getting wrong here..
is it about folders ...

---

### Post by debjit_bis08 on 2008-04-08
Wel wat i was not doing was
not verifying the gmail certificate
this works 
openssl s_client -connect pop.gmail.com:995 -CApath <pathtothecertificates>
mine is /etc/ssl/certs/

---

