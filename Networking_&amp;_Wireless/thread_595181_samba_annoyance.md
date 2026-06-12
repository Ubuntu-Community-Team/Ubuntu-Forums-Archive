---
title: "samba annoyance"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2007-10-28
I recently had to reinstall my OS after a bad gutsy attempt. And now samba is acting funny. While accessing the shares by clicking the link to smb://192.168.1.104/OpenShare I'm warned "The golder contents could not be displayed. Sorry, couldn't display all the contents of "OpenShare". If I then click "OK" then back and then double click the link again, I am allowed in with no complaints. As far as I can tell this problem only occurs the first time after a samba restart.

Any Ideas?


```

[global]
workgroup = CYGNEHOME
netbios name = 192.168.1.104
wins support = no

[OpenShare]
path = /media/sda7/OpenShare
create mask = 777
directory mask = 777
guest ok = yes
writable = yes
```

---

