---
title: "Linux Client for ISA Server?"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by ajkain on 2007-04-04
*** My question:

My company uses M$ ISA server.
How to install linux client for ISA Server?
I have configured my linux to Internet (e.g. proxy in FF) but other programs (pop3, smtp, ftp, ...) doesn't work


*** My dirty solution:

[FONT="Courier New"]Linux  <-->  Windoz with ISA client  <-->  Windoz with ISA server[/FONT]

On my Windoz with ISA client:

I install Cygwin Environment + OpenSSH server ([http://pigtail.net/LRP/printsrv/cygwin-sshd.html](http://pigtail.net/LRP/printsrv/cygwin-sshd.html)).

I configure my ISA Client (WSPCFG.INI and CREDTOOL.EXE).

WSPCFG.INI in C:\cygwin\usr\sbin (SSHD.EXE folder):
[FONT="Courier New"][sshd]
Persistent=1
KillOldSession=1
ForceCredentials=1[/FONT]

[FONT="Courier New"]C:\Program Files\Microsoft Firewall Client\CREDTOOL.EXE -w -n sshd -c myusername mydomainname mypassword[/FONT]
(myusername, mydomainname and mypassword must be ISA server credentials)


On my Linux:

[FONT="Courier New"]ssh -fND1080 myusername:mypassword@mywindozisaclientname[/FONT]
(myusername and mypassword must be an account for Windoz with ISA client)

So I create a dynamic port forwarding (ssh behaves as a socks server).

I configure my mail client program (PROXY SOCKS = localhost , PORT = 1080)

Incredible, it works!!!


I hope this helps somebody, good luck! ;)

---

### Post by true_friend on 2007-04-07
good tweaking but an extra system....is the main problem which would be used as a socks proxy. 
people like me who are at dual boot.. will remain suffering..

---

### Post by brayaldias on 2008-07-13
Is this the same for the linux server also...as it is mentioned its only for linux client...?

My Linux server is behind the ISA server and a remote user wants a SSH connection to the linux server how do v configure the ISA server to forward the SSH request.

Please help us with the steps.

---

