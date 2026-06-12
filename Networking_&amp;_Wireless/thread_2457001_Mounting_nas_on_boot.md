---
title: "Mounting nas on boot"
date: 2021-01-23
forum: Networking &amp; Wireless
---

### Post by moorhead47 on 2021-01-23
Hi All I am trying to mount an nas on boot, I have edited the fstab however this still does not work. 

I have enabled nt1 as the nas is older and only supports smb1.

I have also created a mount point in media/nas

the nas i want to mount is smb://nas/public

I have attached an image of the fstab

---

### Post by Morbius1 on 2021-01-24
> //nas/public /media/nas auto guest,uid=1000,iocharset=utf8 0 0 vers=1.0
Your syntax is messed up. It should look like this:
> //nas/public /media/nas [COLOR=#ff0000]**cifs**[/COLOR] guest,uid=1000,iocharset=utf8[COLOR=#ff0000]**,vers=1.0**[/COLOR] 0 0

And don't forget to do the systemd 2-step:
```
sudo systemctl daemon-reload
```
```
sudo systemctl restart remote-fs.target
```

---

