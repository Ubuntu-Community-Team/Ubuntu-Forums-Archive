---
title: "windows sharing on wired and internet on wireless"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by luckyluca on 2008-02-01
Hello,

As the title says I'm trying to have both wireless and wired working simultaneously on my ubuntu 7.1 64bit laptop.
The idea is to access a windows shared folder on a pc running windowsxp pro using the wired connection,
and access internet using the wireless connection. Since I'm pretty new to networking, how can I do this?

thanks a lot
Luca

config
dell m6300
ubuntu gutsy 7.1 64bit
ipw3945 and nm-applet

---

### Post by luckyluca on 2008-02-02
Ok,

Lets make one step at the time; let's focus on the wireless connection:
I can connect to a windows share using Places->"Connect to Server",
but I would like  to mount it to a specific location.
In other words I would like to have 192.168.100.7/uovo available in /local/uovo
I've tried using 
smbmount but I get the error 
[I]sudo smbmount //192.168.100.7/uovo /mnt/uovo 
Password: 
11190: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed[/I]

Any help would be much appreciated.
Thanks 
Luca


> **luckyluca said:**
> Hello,

As the title says I'm trying to have both wireless and wired working simultaneously on my ubuntu 7.1 64bit laptop.
The idea is to access a windows shared folder on a pc running windowsxp pro using the wired connection,
and access internet using the wireless connection. Since I'm pretty new to networking, how can I do this?

thanks a lot
Luca

config
dell m6300
ubuntu gutsy 7.1 64bit
ipw3945 and nm-applet

---

