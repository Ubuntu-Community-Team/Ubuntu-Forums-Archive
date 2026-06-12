---
title: "how to tell if you are logged in as root"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by baker` on 2009-10-08
I installed Ubuntu 9.04 (first time ever :D) on my laptop using wubi.
When I boot, I log into my user that was made automatically by wubi (I'm assuming).

Could anyone tell me if this means that I am not logged in as root?
Also, what terminal code would let me know if I'm logged in as root?

thanks again,

---

### Post by tarps87 on 2009-10-08
By default you can not login as root on Ubuntu, instead you use sudo

More info here
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To find out who you are logged in as type this in the terminal
```
whoami
```

---

### Post by wojox on 2009-10-08
You're not logged in as root. You do have sudo power.

In the terminal the prompt for root ends with # as opposed to $

---

### Post by philinux on 2009-10-08
> **baker` said:**
> I installed Ubuntu 9.04 (first time ever :D) on my laptop using wubi.
When I boot, I log into my user that was made automatically by wubi (I'm assuming).

Could anyone tell me if this means that I am not logged in as root?
Also, what terminal code would let me know if I'm logged in as root?

thanks again,


The root account is disabled in ubuntu distro.

To use admin rights we use the prefix sudo or gksudo for gui apps.

eg

sudo fdisk -l

gksudo nautilus


Have a browse here. [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by alphaniner on 2009-10-08
Don't know anything about wubi, but if your terminal prompt doesn't begin with```
root@
```then you are not logged in as root.

---

### Post by baker` on 2009-10-08
thanks this has really helped.

i didnt know that root account had been disabled on ubuntu.
reading too many non-ubuntu articles i spose.

---

### Post by philinux on 2009-10-08
> **baker` said:**
> thanks this has really helped.

i didnt know that root account had been disabled on ubuntu.
reading too many non-ubuntu articles i spose.

Go steady with the sudo and especially gksudo nautilus.

You can really bork your system. Double check any commands you're using.

---

### Post by slakkie on 2009-10-08
```

id
echo $UID # if 0 then you are root
echo $USER # if root then ... 
env | grep root


## In action:
id
uid=0(root) gid=0(root) groups=0(root)

echo $UID $USER
0 root

env | grep root
LOGNAME=root
USER=root
USERNAME=root
WHOAMI=root

```

---

