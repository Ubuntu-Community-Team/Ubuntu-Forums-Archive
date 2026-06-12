---
title: "microsoft-ds????"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by nikolaos on 2006-12-10
hi all, i've just started using nmap so my questions might sound a little stupid, well here it goes.
when i type
```
nmap -sF localhost
```   #

i get 
```
Starting Nmap 4.10 ( http://www.insecure.org/nmap/ ) at 2006-12-10 19:27 GMT
Interesting ports on localhost (127.0.0.1):
Not shown: 1674 closed ports
PORT    STATE         SERVICE
22/tcp  open|filtered ssh
53/tcp  open|filtered domain
139/tcp open|filtered netbios-ssn
445/tcp open|filtered microsoft-ds
631/tcp open|filtered ipp

Nmap finished: 1 IP address (1 host up) scanned in 1.454 seconds

```

is there anything wrong with port 445?? 
What is microsoft-ds?

thanks in advance.

---

### Post by dbott67 on 2006-12-10
It's for Microsoft Directory Services.
>     Microsoft-DS Service is used for resource sharing on Windows 2000, XP, 2003, and other samba based connections.  This is the port that is used to connect file shares for example.

It is the replacement for the old 137-139 ports in previous versions of Windows.

-Dave

---

### Post by bscbrit on 2006-12-10
This is the port used for samba.  See this link:

[http://www.grc.com/port_445.htm](http://www.grc.com/port_445.htm)

though for more information.

---

### Post by nikolaos on 2006-12-10
very informative article, thanks.

---

