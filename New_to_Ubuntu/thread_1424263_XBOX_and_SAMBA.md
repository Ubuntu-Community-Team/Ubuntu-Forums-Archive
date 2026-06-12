---
title: "XBOX and SAMBA"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Saito Chikara on 2010-03-07
I am trying to backup my Xbox games directly onto my computer, because I only have 3 gigs free on my xbox. So, i downloaded SAMBA for my Ubuntu (9.10) and i am trying to figure out how to SAMBA from my dvd2xbox app directly to a folder on the desktop of my computer. How do I go about this?

Thanks!

(If I don't have a specific enough of a description, tell me what you need and I'll add it.)

---

### Post by Fenris_rising on 2010-03-07
Have a look on the afterdarkforums under xbox for all the info you could wish for. I rip my game disks on my PC then FTP them to the xbox as and when i need.

regards

Fenris

---

### Post by Saito Chikara on 2010-03-07
I checked out AfterDawn forums, and I can't find anything to help with my Ubuntu end... Does anyone else have any ideas??

---

### Post by 3rdalbum on 2010-03-07
For the Ubuntu end, install the 'system-config-samba' package. Then go to System > Administration > Samba and set up a shared folder. Then you will be able to access your share from anywhere on your network.

---

### Post by Saito Chikara on 2010-03-09
Okay, I think I have my .conf file setup right...


```

[global]
workgroup = workgroup
netbios name = ******
server string = %h server (Samba, Ubuntu)
log file = /var/log/samba/log.%m
max log size = 50
map to guest = bad user
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
dns proxy = no

[public]
path = /root/XBOX
public = yes
only guest = yes
writable = yes

[XBOX]
path = /root/XBOX
writeable = yes
browseable = yes
guest ok = yes
```
But what do I need to set my "smb://" to, on my xbox? what's the format? I'm thoroughly confused.

---

