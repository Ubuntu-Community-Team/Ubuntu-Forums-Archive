---
title: "Samba share mounts in Ubuntu, doesn't in XP"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by nickoli_02 on 2008-02-09
I have samba set up on one Ubuntu box to share a folder over a local network. I can mount it on my laptop in Ubuntu, but I can't map the folder as a network drive in Windows. The error is as follows:

```
The network path \\192.168.1.104\media could not be found.
```

As I said I can mount the shared folder when my laptop is booted into Ubuntu so the firewall is clear and all that good stuff. I've tried searching the forum for a fix but haven't been successful. Here is the output of testparm:

```
admin-1@server-1:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[media]"
Loaded services file OK.
WARNING: passdb expand explicit = yes is deprecated
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions


[global]
workgroup = SMB1
server string = media server
null passwords = no
pasdb backend = tdbsam
username map = /etc/samba/smbusers
syslog only = Yes
announce version = 5.0
name resolve order = hosts wins bcast
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

[media]
comment = Media share folder
path = /home/admin-1/media
force user = admin-1
force group = admin-1
read only = No
create mask = 0777
directory mask = 0777
case sensitive = Yes
fstype = Samba
```

---

### Post by nickoli_02 on 2008-02-10
hate to do this, but...

bump

---

### Post by nickoli_02 on 2008-02-10
Well I found the problem, I'm using ZoneAlarm's firewall instead of XP's generic firewall and it was blocking the connection. All is well now :)

---

