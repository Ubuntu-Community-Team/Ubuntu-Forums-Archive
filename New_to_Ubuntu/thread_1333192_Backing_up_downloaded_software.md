---
title: "Backing up downloaded software"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by jenif on 2009-11-21
How to backup the software i have downloaded using the add or remove programs of Ubuntu?

I have downloaded a few software for Ubuntu. but my friend doesn't have net connection. i want to give these software to her. how should i do that?

---

### Post by gn2 on 2009-11-21
You can use APTonCD to make a CD/DVD with your downloaded applications on it and the applications can be installed from it.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I think it's in the Ubuntu repositories and you can install it through Add/Remove, Synaptic or the good old fashioned terminal way:
```
sudo apt-get install aptoncd
```

---

### Post by jenif on 2009-11-21
Thank you. it works.

---

### Post by frenchn00b on 2009-11-21
> **jenif said:**
> How to backup the software i have downloaded using the add or remove programs of Ubuntu?

I have downloaded a few software for Ubuntu. but my friend doesn't have net connection. i want to give these software to her. how should i do that?

put the /var/cache/apt/archives 
all those deb into /home/debian
n put all those deb into pool  something
 
and  
check my scripts to maek sthg for your sources.list :

> #!/bin/sh

##
cat /etc/apt/sources.list
echo "Hello Create from the pool the packages, from contrib and contribx"
echo " Type sources.list, to add and update your sources.list"
echo "type in arg1 install if you want to install. not choosen"
printf "Enter the distro name >"
read distroname



if   [ "$1"  == "install" ]  ; then
      echo "deb file:/home/debian/ $distroname contrib" >> /etc/apt/sources.list
        cat /etc/apt/sources.list
        exit
        exit
        exit 0
fi

ls pool/

mkdir -p /home/debian/pool
mkdir -p /home/debian/dists
cd /home/debian ; rm  dists/$distroname/contribx/binary-i386/Packages   ;   mkdir -p dists/$distroname/contrib/binary-i386/  ; apt-ftparchive  packages pool/contrib/ > dists/$distroname/contrib/binary-i386/Packages
#



---

