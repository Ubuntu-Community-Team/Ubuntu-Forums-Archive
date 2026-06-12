---
title: "netcat connection refused."
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by ejohn on 2008-06-09
hi guys

i tried to setup nc to listen on port 1234. but i keep getting error saying connection refused.

nc -l 1234

nc localhost 1234
localhost [127.0.0.1] 1234 (?) : Connection refused

what could be the reason? firewall?

---

### Post by whitey on 2008-06-09
Hello,

What I would do first is use the following command to see if you daemon is actually listening on the port your think:

netstat -ntpl

---

### Post by ejohn on 2008-06-09
this is what netstat -ntpl returned..

tcp        0      0 0.0.0.0:36922           0.0.0.0:*               LISTEN      7369/nc 

does that mean its not listening on 1234 as specified? anyway tried connecting to 36922. geting the same error.

---

### Post by ejohn on 2008-06-09
thanks a lot whitey.

that netstat thing got me thinking correctly.

it worked when i started nc as follows..
nc -l -p 1234 localhost

---

### Post by whitey on 2008-06-09
awesome, glad to help

:KS

---

### Post by skiet078 on 2011-09-07
error is 
connection refused when i issue this command
nc -vvn 192.1168.138.135 4444

---

