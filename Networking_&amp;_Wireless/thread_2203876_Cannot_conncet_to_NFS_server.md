---
title: "Cannot conncet to NFS server"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by lucipher on 2014-02-05
Hi,

I have an Ubuntu server and configured NFS sever, but it is not possible to access from any machine in the same network. The server respond to ping, ssh access. When I run nmap from any machine in the network (server is 192.168.0.10):

```

nmap 192.168.0.10

PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
88/tcp   open  kerberos-sec
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
389/tcp  open  ldap
443/tcp  open  https
445/tcp  open  microsoft-ds
464/tcp  open  kpasswd5
631/tcp  open  ipp
636/tcp  open  ldapssl
1024/tcp open  kdm
2222/tcp open  EtherNet/IP-1
3268/tcp open  globalcatLDAP
3269/tcp open  globalcatLDAPssl


```

But if I run it **from** the server:

```

nmap 192.168.0.10

PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
88/tcp   open  kerberos-sec
111/tcp  open  rpcbind
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
389/tcp  open  ldap
443/tcp  open  https
445/tcp  open  microsoft-ds
464/tcp  open  kpasswd5
631/tcp  open  ipp
636/tcp  open  ldapssl
1002/tcp open  windows-icfw
1024/tcp open  kdm
2049/tcp open  nfs
3268/tcp open  globalcatLDAP
3269/tcp open  globalcatLDAPssl
6566/tcp open  unknown


```

When I run showmount **from** the server:

```

showmount -e 192.168.0.10
Export list for 192.168.0.10:
/srv/compartida/isos      192.168.0.0/24
/srv/compartida/peliculas 192.168.0.0/24
/srv/compartida/musica    192.168.0.0/24

```

From any other machine I get a time out error.

```

showmount -e 192.168.0.10
clnt_create: RPC: Port mapper failure - Timed out

```

Here's the **/etc/exports** file

```

/srv/compartida/musica 192.168.0.0/24(rw,sync,no_root_squash)
/srv/compartida/peliculas 192.168.0.0/24(rw,sync,no_root_squash)
/srv/compartida/isos 192.168.0.0/24(rw,sync,no_root_squash)

```

It seems to me that for some reason NFS port is blocked for external use (outside the server) but I don't know why.

I used: 
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)
[https://help.ubuntu.com/12.04/serverguide/network-file-system.html](https://help.ubuntu.com/12.04/serverguide/network-file-system.html)

And some others that I can't remember, but this 2 worked dis the basic job.

If you have any clue, I'd appreciate it very much

---

### Post by SeijiSensei on 2014-02-05
Have an iptables firewall on the server?  If so, you probably don't have port 2049 open.

---

### Post by lucipher on 2014-02-06
Thaks for yous answer, that resolved my problem. I just didn't noticed that the fw was blocking that port in my server.

Cheers.

---

### Post by SeijiSensei on 2014-02-06
Any time you can connect to a service from the server itself, but not from a remote client, the firewall is the first thing to check.

Glad I could help.

---

