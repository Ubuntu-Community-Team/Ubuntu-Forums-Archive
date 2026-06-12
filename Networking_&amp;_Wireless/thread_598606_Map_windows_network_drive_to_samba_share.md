---
title: "Map windows network drive to samba share"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by Arbiter on 2007-10-31
Hello all,

I have an ubuntu machine that i'm using as a intranet web server on a network that uses a Windows Server 2003 domain controller.  I want to set one of the windows machines on the network to map a network drive to a samba share.  is this possible?

Thanks in advance,

arbiter

---

### Post by Prospero2006 on 2007-10-31
First, on the linux machine:
```

apt-get install samba

```

Sounds like you already did this.

Let's assume the following:
Linux IP: 192.168.1.10
Win IP: 192.168.1.20

On the linux machine open up /etc/samba/smb.conf

Create an entry like this:
```

[downloads]
   comment = downloads
   path = /downloads
   guest ok = no
   browseable = yes
   create mask = 0777
   directory mask = 0777

```
This little chunk assumes I have a directory called /downloads

Do  an smbd restart 

Go to the windows machine:
Right Click on My Computer
Choose 'Map Network Drive'
Type:
\\192.168.12.10\downloads

It should prompt you for a username and password, which you'll need to set 
up on the linux box with 
```

smbpasswd -a username

```

I hope that helps
Pros

---

### Post by Arbiter on 2007-10-31
This set me on the right track - thanks! :)

---

