---
title: "What is the default ident daemon?"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by googlegot on 2007-10-10
I have been trying to install pidentd and have been coming up with this error :

```
[Pidentd, version 3.0.19 (compiled for Linux 2.6.15.7) - Dec 21 2006 07:19:50]
identd: failed binding to the TCP/IP socket
```

Ive come to the conclusion that I have another ident daemon running, but being the linux noob I am, I have no clue what it is or where to find it.  Any help is appreciated.

---

### Post by noob12 on 2007-10-10
Running 
```

sudo lsof -i

```
will tell you which processes are listening on which ports.

If you are running a version of inetd, check the confs for an "auth" or "ident" service.

---

### Post by googlegot on 2007-10-10
Thanks for the reply :p that didnt do much for me, there is no program listening on port 113, so I'm thinking its integrated into some network daemon.  Does anyone out there know what ident daemon is running by default in x86_64 fiesty?

---

