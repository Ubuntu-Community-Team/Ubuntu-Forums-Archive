---
title: "telnet failure"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by rosegal on 2010-03-05
hey thr..i have tried using d command u gv..there was no change though so i assume its working..i proceeded to another step which is telneting..but gt stuck again as usual..

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

it just stopped here..i cant proceed anything after this again..i check the mail daemon and got this errors :

Mar  5 13:39:50 royth-laptop postfix/master[2495]: warning: process /usr/lib/postfix/smtpd pid 6413 exit status 1
Mar  5 13:39:50 royth-laptop postfix/master[2495]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

any idea as a solution...
pls help me!!!!!!!!!!!

---

### Post by Gone fishing on 2010-03-06
Why telnet when you could ssh?

ssh user@192.168.1.1 (or whatever IP address)

if you what to open graphical stuff

ssh -X -C user@192.168.1.1

---

### Post by rosegal on 2010-03-06
hello..i did ssh and got this ...

ssh: connect to host 10.xxx.x.xx port 22: Connection refused

any idea???

---

### Post by HermanAB on 2010-03-06
Install the ssh-server (sshd) package and open port 22 in your firewall if required.

---

