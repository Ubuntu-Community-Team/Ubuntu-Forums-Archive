---
title: "SAMBA PITA: i think i found the problem, now I need a solution"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2007-09-07
servers terminal
```
antsvr@antubuntu:~/batch$ hostname
antubuntu

```

client terminal
```
ant2ne@ant2ne-laptop:~$ smbclient //antubuntu/OpenShare
Connection to antubuntu failed
ant2ne@ant2ne-laptop:~$ smbclient //192.168.1.104/OpenShare
Password: 
Domain=[ANTUBUNTU] OS=[Unix] Server=[Samba 3.0.24]
smb:\>
```

my current smb.conf
```
[global]
workgroup = CYGNEHOME

[OpenShare]
path = /media/sda7/OpenShare
guest ok = yes
read only = no

[SecureShare]
path = /media/sda7/SecureShare
read only = yes
write list = antsvr, ant2ne
```
Seems to be a name problem. Now *sometimes* the client will connect by name, but not often. But it seems IP connects every time. Problem is, the Windows machines in the workgroup don't use a smbclient log on, so they can't access the share at all.

Ideas?

---

### Post by HermanAB on 2007-09-07
It looks like a DNS configuration issue to me.  Not necessarily on the DNS server, but on the Windows clients.

Ensure that the name resolves and that the best server is named first and that the search parameter is defined so that DNS can find unqualified hostnames.

Play with nslookup and dig to figure out what is going wrong.

Cheers,

H.

---

### Post by ant2ne on 2007-09-07
> **HermanAB said:**
> Ensure that the name resolves and that the best server is named first and that the search parameter is defined so that DNS can find unqualified hostnames.
How?

I don't have a DNS Server. This is (currently) a Windows workgroup.  And the two windows PCs are Home Edition. I do plan to get my Pro Edition on there, and then (later) install an 03 Server. But for right now, baby steps.

Toying on the Win machine, typing \\192.168.1.104\OpenShare into the address of the Window explorer does connect to the share. So this is a "fix", but I'd like to get it to work by name also.

On a side note, I mistyped "\\192.168.1.104\" as "//192.168.1.104" and apache told me "It Works" I guess I can skip the first two chapters on installation and setup of Apache in the book I got from the library. You loose some you win some.

---

### Post by ant2ne on 2007-09-09
bump

---

### Post by Zorael on 2007-09-09
You could manually add the IPs to the hosts files on both systems, I guess. /etc/hosts in linux and, uh, C:\Windows\system32\drivers\etc\hosts in Windows.

---

