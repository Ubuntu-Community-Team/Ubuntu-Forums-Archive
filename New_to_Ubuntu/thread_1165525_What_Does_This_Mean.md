---
title: "What Does This Mean?"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by jhtracy on 2009-05-20
Every time I try and update my system I get this series of messages.  What do they mean and how do I get rid of them???





Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by raymondh on 2009-05-20
try system > admin > software sources (you'll need your passowrd) and untick the cd-rom

and then in a terminal,

```
sudo apt-get update
sudo apt-get upgrade
```

hope this helps

Regards,

---

### Post by abn91c on 2009-05-20
you have a CDrom enabled as a repository in synaptic, go to software sources>third party tab and uncheck the cdrom line, then proceed with your updates as usual.

---

### Post by jhtracy on 2009-05-20
> **abn91c said:**
> you have a cdrom enabled as a repository in synaptic, go to software sources>third party tab and uncheck the cdrom line, then proceed with your updates as usual.
thank you!!!!!

---

