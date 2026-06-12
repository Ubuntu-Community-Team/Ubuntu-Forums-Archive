---
title: "2 networking problems"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by Hig on 2005-08-15
Problem the first:

When I start my laptop, the samba service doesn't start by default. If I run 'sudo /etc/init.d/samba start' everything works fine

Problem the second:

When I attempt to log in to a samba share from a windows machine I get asked for a password and username even though on other ubuntu machines I can log in with none.
smb.conf:
```
[global]
server string = Ubuntu Server
workgroup = Workgroup
netbios name = Server
security = SHARE

[general]
path = /mnt/local/hdc1
available = yes
browseable = yes
public = yes
writable = yes

[finished]
path = /mnt/local/hdd1
available = yes
browseable = yes
public = yes
writable = yes

```

And a third non-networking problem. I have remote desktop preferances set to allow VNC desktop connections, but I always get connection refused.

---

### Post by amohanty on 2005-08-15
> When I start my laptop, the samba service doesn't start by default. If I run 'sudo /etc/init.d/samba start' everything works fine 

Try BUm (boot up manager), kinda like serviceconf in RH8.

---

