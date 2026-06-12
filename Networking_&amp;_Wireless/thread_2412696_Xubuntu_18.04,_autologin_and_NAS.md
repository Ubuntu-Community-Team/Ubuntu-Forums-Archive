---
title: "Xubuntu 18.04, autologin and NAS"
date: 2019-02-16
forum: Networking &amp; Wireless
---

### Post by m.strajnar on 2019-02-16
Hello.

I have HTPC setup with Xubuntu-core 18.04.
As this is HTPC I need it to autologin at startup and auto mount NAS storage through WiFi.

Autologin is set up with /etc/lightdm/lightdm.conf

```
[SeatDefaults]
autologin-user=****
autologin-user-timeout=0
user-session=xfce
greeter-session=lightdm-gtk-greeter
```

Mount is set up in /etc/fstab

```
//192.168.1.***/nas   /mnt/NAS   cifs    username=****,password=****,rw,vers=1.0,_netdev,uid=1000,gid=1000,file_mode=0777,dir_mode=0777    0   0
```

Problem is that every reboot I make I have to **insert password for NAS** if I want to access it.
If I remove autologin and **login to xfce manually**, then everything works fine.

How to fix this?

---

