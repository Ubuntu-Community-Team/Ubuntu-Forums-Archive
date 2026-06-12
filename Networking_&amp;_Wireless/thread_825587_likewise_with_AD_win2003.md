---
title: "likewise with AD win2003"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by fisho on 2008-06-11
Hi all i get this error when trying to connect ubuntu to win2003


Error: Manual configuration required [code 0x00080043]

The configuration stage 'open ports to DC' cannot be completed automatically.
Please manually perform the following steps and rerun the domain join:

Some required ports on the domain controller could not be contacted. Please
update your firewall settings to ensure that the following ports are open to
'abc123.com':
    88  UDP
    137 UDP
    389 UDP
    464 UDP
    123 UDP
    88 TCP
    139 TCP
    389 TCP
    445 TCP
    464 TCP
xx@raptor:~$ 

is this error on my win 2003 box not allowing ubuntu ro connect?

---

### Post by nixscripter on 2008-06-11
It sounds like it.

One simple way to find out, assuming it's your server (other people will think you're trying to hack them or something) is to install **nmap** (from Synaptic package manager) and run a port scan: ```
nmap -p U:88,137,389,464,123,T:88,139,389,445,464 **winxp-machine-ip**
```

---

### Post by lsutiger on 2008-06-20
I am having the same problem. Here is the output of that command:
```
 nmap -p U:88,137,389,464,123,T:88,139,389,445,464 192.168.1.15

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-20 15:37 CDT
Interesting ports on 192.168.1.15:
PORT    STATE SERVICE
88/tcp  open  kerberos-sec
139/tcp open  netbios-ssn
389/tcp open  ldap
445/tcp open  microsoft-ds
464/tcp open  kpasswd5

Nmap done: 1 IP address (1 host up) scanned in 0.094 seconds

```

---

### Post by redmansk8 on 2008-06-20
I had the same problem but I was connecting to a win 2000 server with active directory! Never found an answer to the problem.

---

### Post by nixscripter on 2008-06-20
According to this: [http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-April/000371.html](http://lists.likewisesoftware.com/pipermail/likewise-open-discuss/2008-April/000371.html)

I think the UDP ports need to be open. I notice, lsutiger, you've got TCP ports open. Try getting rid of the T: part, and stick to the U: part.

---

