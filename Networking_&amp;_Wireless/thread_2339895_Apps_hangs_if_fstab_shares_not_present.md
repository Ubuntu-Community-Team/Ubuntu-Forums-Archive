---
title: "Apps hangs if fstab shares not present"
date: 2016-10-13
forum: Networking &amp; Wireless
---

### Post by razor7 on 2016-10-13
Hi! I'm experiencing a rare issue here.

I have a ubuntu 16.04 server with CIFS working. In my desktop PC I have ubuntu 16.04, and I do automount the server CIFS shares at boot through fstab with this two entries:
```

//server.name/storage /media/storage cifs x-systemd.automount,_netdev,credentials=/etc/samba/credentials,uid=martin,gid=martin,iocharset=utf8,file_mode=0644,dir_mode=0755 0 0
//server.name/server  /media/server   cifs x-systemd.automount,_netdev,credentials=/etc/samba/credentials,uid=martin,gid=martin,iocharset=utf8,file_mode=0644,dir_mode=0755 0 0

```

The issue arises when my server box is down, at that time, if I boot my desktop PC, I think it tryes to mount the CIFS shares somehow and fails, then, some apps start to fail:
[LIST]
[*]Sometimes Nautilus lags a lot to open
[*]Gedit lags for about 15 to 20 second to open blank file
[*]Libreoffice hangs and gets grey screen and unresponsive
[/LIST]

If I reboot my desktop PC with that two fstab entries commented, then there are no hangs at all...

I thought that by adding x-systemd.automount I could have that shares on hold until some app calls for it, but it still fails!

Thanks in advise!

---

### Post by razor7 on 2016-10-14
Following the ARch linux Wiki i have done some mods to my fstab entries with no luck!

```
//server.name/server  /media/server  cifs noauto,nofail,x-systemd.automount,x-systemd.requires=network-online.target,x-systemd.device-timeout=20,credentials=/etc/samba/credentials,uid=martin,gid=martin,iocharset=utf8,file_mode=0644,dir_mode=0755 0 0
```

---

