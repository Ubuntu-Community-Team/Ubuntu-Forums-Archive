---
title: "Ubuntu &lt;-&gt; Ubuntu &lt;-&gt; Windows samba configuration"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by rozbarwinek on 2008-10-01
I got 2 computers, on PC-1 (that is sharing internet to PC-2) I got windows xp and ubuntu 8.04 installed, and on PC-2 I have only untu 8.04
I have configured samba so when on PC-1 is running windows there's no problem with sharing files.
I can see files from PC-2 on PC-1 and vice versa but when I'm running ubuntu on both computers they can't see each other, there is internet connection on PC-2 but I can't share files between them.

Here's my samba configuration on both ubuntu's -->

```
[global]
    netbios name = emil
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    username map = /etc/samba/smbusers
    usershare allow guests = Yes
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no
```

---

### Post by superprash2003 on 2008-10-01
ensure that no firewall is blocking .. ensure that the two machines can ping each other.. have you installed samba on both machines?? to connect.. go to places->computer and under goto type smb://x.x.x.x where x.x.x.x is the ip of the machine you want to connect to

---

### Post by rozbarwinek on 2008-10-01
> **superprash2003 said:**
> ensure that no firewall is blocking .. ensure that the two machines can ping each other.. have you installed samba on both machines?? to connect.. go to places->computer and under goto type smb://x.x.x.x where x.x.x.x is the ip of the machine you want to connect to

Yes I have installed samba on both computers, they can ping each other and when I go to smb://192.168.0.2 I can see other computer shares :)
On the PC-1 I have firestarter running.
So what can I do to see them in the network section?

---

