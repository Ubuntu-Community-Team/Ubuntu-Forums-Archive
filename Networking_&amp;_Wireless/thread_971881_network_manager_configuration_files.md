---
title: "network manager configuration files"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by ruixordo on 2008-11-05
Hi people

Someone knows where are nm configuration files? I don't find where my config was stored.

I don't understand why ubuntu developers dedided to abandon /etc/network/interfaces
lost debian compatibility is a bad way, no doubt

---

### Post by pedro_orange on 2008-11-05
What are you trying to achieve?

Doesn't nm use gconf now?

```
gconf-editor
```

---

### Post by ruixordo on 2008-11-05
> **pedro_orange said:**
> What are you trying to achieve

lol
I'm trying to understand how works my OS :P

> **pedro_orange said:**
> Doesn't nm use gconf now?
gconf? arggg... my net config should be out there...gconf is like windows registry :D

---

### Post by COKEDUDE on 2011-01-10
The user settings will be stored here. 

```
/home/userdirectory/.gconf/system/networking/connections
```

[http://www.arachnoid.com/linux/NetworkManager/](http://www.arachnoid.com/linux/NetworkManager/)

The System settings will be stored here. 


```
/etc/NetworkManager
```
```
/etc/NetworkManager/system-connections
```

---

