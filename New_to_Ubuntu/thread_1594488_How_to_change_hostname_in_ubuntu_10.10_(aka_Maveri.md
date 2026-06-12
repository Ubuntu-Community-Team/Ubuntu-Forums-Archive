---
title: "How to change hostname in ubuntu 10.10 (aka Maverick Meerkat)"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Rushyang on 2010-10-12
Hey guys,

I went through some tutorial in which they say to change oldhostname, replace newhostname throughout /etc/hostname and /etc/hosts files. and then finally stop and start /etc/init.d/hostname.sh service.

But when I try to execute /etc/init.d/hostname.sh stop. 
It says hostname.sh was not found. And that script does no exist there. So how to change the hostname permanently?

---

### Post by CharlesA on 2010-10-12
you need to edit two files:

```
sudo nano /etc/hostname
```

```
sudo nano /etc/hosts
```

Change the old hostname to the new and reboot.

hostname.sh doesn't exist in Ubuntu.

---

### Post by PapaNerd on 2010-10-12
You may want to update:
/etc/motd
/etc/printcap

Also, be sure to update any ssh keys you have created.

---

### Post by Rushyang on 2010-10-13
> **CharlesA said:**
> you need to edit two files:

```
sudo nano /etc/hostname
``````
sudo nano /etc/hosts
```Change the old hostname to the new and reboot.

hostname.sh doesn't exist in Ubuntu.


Alright, I just didn't reboot ubuntu.. that's why I was getting confused. Thanks for the reply.. I get it.

---

### Post by yetiman64 on 2010-10-13
To set the hostname without a reboot it is possible to do,
```
sudo hostname -F /etc/hostname
``` after 1st altering the 2 files mentioned by CharlesA.

---

