---
title: "Can't connect to NFS shares"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by jlparsons on 2016-01-26
I've done a fresh install of ubuntu server lts on my nas server and have shared two directories via nfs by following the guidelines on help.ubuntu.com and entering;
```
/sharefolder  *(ro,sync,no_root_squash)
```
in /etc/exports for each directory to be shared.

Running "showmount -e localhost" on the server then shows both the directories;
```
Export list for localhost:/sharefolder *
```

However, running showmount -e 192.168.my.server on my linux mint cinamon 17.3 client gives the following error;
```
clnt_create: RPC: Port mapper failure - Unable to receive: errno 113 (No route to host)
```

Running nmap on server on itself gives the following;
```
Starting Nmap 6.40 ( http://nmap.org ) at 2016-01-26 11:33 GMTNmap scan report for 192.168.0.8
Host is up (0.00080s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
49152/tcp open  unknown
```

And running nmap on the client at the server gives the following;
```
Starting Nmap 6.40 ( http://nmap.org ) at 2016-01-26 11:25 GMT
Nmap scan report for 192.168.0.15
Host is up (0.0024s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
2049/tcp open  nfs
```

Whereas running nmap on the client on itself gives;
```
Starting Nmap 6.40 ( http://nmap.org ) at 2016-01-26 12:18 GMTNmap scan report for localhost (127.0.0.1)
Host is up (0.0000060s latency).
Not shown: 995 closed ports
PORT      STATE SERVICE
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
631/tcp   open  ipp
49152/tcp open  unknown
```

And running nmap on the server at the client gives;
```
Nmap scan report for 192.168.0.8
Host is up (0.00080s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
445/tcp   open  microsoft-ds
49152/tcp open  unknown
```

So, I'm at a bit of a loss here!  Anyone have any thoughts?  Don't really want to give up and go back to samba.

---

### Post by jlparsons on 2016-01-26
Solved - needed to allow ports under UFW!

---

