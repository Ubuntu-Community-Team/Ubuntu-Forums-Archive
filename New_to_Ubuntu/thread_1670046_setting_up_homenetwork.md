---
title: "setting up homenetwork"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Alfrmor on 2011-01-18
Hi I am new to Ubuntu and trying to setup a home network through samba. i have tried to follow Howto's but cannot get the xp client to log on to the ubuntu server. I want the server as a remote document storage and to use the printer which is connected to the ubuntu machine through usb. My ubuntu release is 10.04

---

### Post by cariboo on 2011-01-18
This is how I've got my shared directories setup in /etc/samba/smb.conf

```
[Movies]
	comment = Ripped DVDs
	path = /media/green
	browseable = yes
	read only = no

```

All systems on my network have read/write access to the shares.

---

### Post by cariboo on 2011-01-18
This is how I've got my shared directories setup in /etc/samba/smb.conf

```
[Movies]
	comment = Ripped DVDs
	path = /media/green
	browseable = yes
	read only = no

```

All systems on my network have read/write access to the shares.

---

### Post by Morbius1 on 2011-01-18
> i have tried to follow Howto's but cannot get the xp client to log on to the ubuntu server.
Since you've already tried to use Samba you might want to post the output of the following commands so everyone can see what you've done so far:
```
testparm -s
```
```
net usershare info --long
```

---

