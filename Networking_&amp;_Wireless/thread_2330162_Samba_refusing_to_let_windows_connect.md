---
title: "Samba refusing to let windows connect"
date: 2016-07-08
forum: Networking &amp; Wireless
---

### Post by emielleon on 2016-07-08
Ok so i got this little problem here.
i have made this samba share with 2 shares. Config below
```

[global]  log level = 1
  socket options = TCP_NODELAY
  preferred master = no
  oplocks = no
  security = share
  guest account = root
  workgroup = WORKGROUP
  load printers = no
  netbios name = VuPlus
  log file = /tmp/smb.log


[Nas]
  path = /media/OPSLAG/Emiel
  comment = nas root
  writeable = yes
  valid users = nas root
  browsable = yes
  guest ok = no


[VuPlus]
  path = /media/OPSLAG
  comment = vuplus dir
  writeable = yes
  valid users = nas
  browsable = yes
  guest ok = no



```
i chmoded 777 the directories, and when i try to login with 'root' it works, but with 'nas' it doesn't? I made both accounts using smbpasswd and enabled them. Can somebody help?

---

