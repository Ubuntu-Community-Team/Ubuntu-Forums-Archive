---
title: "samba Private share"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by nousefreak on 2008-06-03
Hi,

I'm having some problems setting up my samba server.
What I want:
Public: readonly (works)
Transfer: read write for everyone
Private: login with read write

```
[global]
; General server settings
  netbios name = SERVER
  server string = SERVER
  workgroup = DELOTUS
  announce version = 5.0
  socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
  guest ok = yes

  ;hosts allow = 127.0.0.1 192.168.1.2 192.168.1.10 192.168.1.100 192.168.1.110 192.168.1.111 192.168.1.11 192.168.1.12 192.168.1.13 192.168.1.16 192.168.1.20 192.168.1.47
  ;hosts deny = 0.0.0.0/0

  passdb backend = tdbsam
  security = share
  null passwords = true
  username map = /etc/samba/smbusers
  name resolve order = hosts wins bcast
  wins support = yes

  printing = CUPS
  printcap name = CUPS

  syslog = 1
  syslog only = yes

[Public]
    path = /home/dries/Share/Public
    ;browseable = yes
    public = yes
    read only = yes
    create mask = 0644

[Private]
    path = /home/dries/Share/Private
    valid users = dries
    security = share
    public = no
    writable = yes
    printable = no
    force user = dries
    force group = dries

[Postbus]
    path = /home/dries/Share/Postbus
    comment = Postbus om bestanden te delen
    public = yes
    read only = no

```

---

