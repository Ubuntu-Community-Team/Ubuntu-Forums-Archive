---
title: "disabling wired eth0 in Kubuntu Lucid 10.04 LTS?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by Butthead on 2010-05-09
Hi,  

Probably a dumb question, but does anyone know how to shut down a wired Ethernet connection in Kubuntu Lucid Lynx 10.04 LTS?  Mine seems to stay connected all the time?  Thanks for any help!

---

### Post by Sealbhach on 2010-05-09
It might sound flippant, but I just pull out the cable from my laptop. I see what you mean though, if you right-click on the network icon it allows you to disconnect wireless, and leave the wired connection, but not the other way around.

.

---

### Post by Butthead on 2010-05-09
My rig is a Desktop though with a very hard to reach (and securely locked in) Ethernet cable. :p

---

### Post by Sealbhach on 2010-05-09
Try

```
ifdown eth0

```

To bring it back up

```
ifup eth0
```
.

---

### Post by Butthead on 2010-05-10
Actually, the commands are:

sudo ifconfig eth0 down

and 

sudo ifconfig eth0 up

Typing in "ifdown eth0" just reports that the interface "eth0" can't be found.

Thanks for the help though! :guitar:

---

