---
title: "&quot;Need to Install Kernell&quot; Error and Resolution"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by iduggan on 2010-05-13
Hello,
I have a Dell 1505 Insperon with both Windows Vista and Ubuntu 9.10.  I was using Ubuntu and it crashed for some reason, when I attempted to start up my computer in lynux again, i received the error "You need to install the kernel first.  
What do I have to do to resolve this issue? And will it completely destroy everything I had on there?

---

### Post by nothingspecial on 2010-05-13
If you really have lost your kenel :shock:

You are going to have to use a live cd. chroot and install a kernel from there.

Boot a live cd

Open a terminal

run ```
fdisk -l
```

Figure out which partition Ubuntu resides on.
```

mkdir buntu
mount -t ext4 /dev/sd[COLOR="Red"]??[/COLOR] buntu
chroot buntu
apt-get update && apt-get upgrade
apt-get install linux-image-generic
```

Change the red question marks to what you have discovered using fdisk -l
No promises on this one, but if you haven`t got a kernel I can`t think of another way without a reinstall.

EDIT **** you`ll probably have to sudo all that lot by the way ***** EDIT

---

