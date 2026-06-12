---
title: "Internet connection"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by ADBD on 2008-03-08
Hi,
I was looking for a tutorial on how to connect to the internet (with wired connection) on ubuntu but couldn't find one (usually it's stickied to the support forums?). 
I have zenwalk linux now and in it it's as easy as typing "pppoe-setup" (to setup) and "pppoe-start" (to start) to terminal. I tried to get my connection working on the ubuntu live co to no avail. Can someone give instructions on how to setup my WIRED connection with no router?

---

### Post by SpaceTeddy on 2008-03-08
configuration is done via
```
sudo pppoeconf
```

then you can either use network manager, or issue this command to dial
```
sudo pon dsl-provider
```

and this one to disconnect
```
sudo poff
```

---

### Post by ADBD on 2008-03-08
Thanks but I got it workin myself before reading your post with sudo ifconfig eth0 and sudo dhclient eth0

what's this?:
ubuntu@ubuntu:~$ sudo pppoeconf
WARNING: Error inserting slhc (/lib/modules/2.6.22-14-generic/kernel/drivers/net/slhc.ko): Bad address
WARNING: Error inserting ppp_generic (/lib/modules/2.6.22-14-generic/kernel/drivers/net/ppp_generic.ko): Bad address
WARNING: Error inserting pppox (/lib/modules/2.6.22-14-generic/kernel/drivers/net/pppox.ko): Bad address
FATAL: Error inserting pppoe (/lib/modules/2.6.22-14-generic/kernel/drivers/net/pppoe.ko): Bad address
Please install ppp package and enable pppoe support in the kernel, or install pppoe package!
Press return to continue...
read: 71: arg count

---

### Post by SpaceTeddy on 2008-03-08
this means that the pppoe (ppp ?) package is not installed. you need to install it before you can use it.

use
```
sudo apt-get install pppoe ppp
```

i think... at least :)

---

