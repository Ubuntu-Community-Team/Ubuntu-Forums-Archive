---
title: "X issue"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by darkeye123 on 2010-01-19
Hey everyone.

I just installed arch Linux on my pc. it wasn't nearly as hard to install as I thought it would be, and I am able to connect to my wireless now. 

However I am having some issues regarding xorg... Namely that my mouse and keyboard do not work as soon as I use xinit. 

I tried this in both lxde and plain x,but to no avail. 

I have setup x using x -configure, and copied the file into x11.

I know this is an ubuntu forum, but I wanted to ask here, since you guys have never let me down.

What should I do?

P.s. I have to use iwconfig to manually connect to wifi... Is there a way to run these commands on startup?

---

### Post by Speed Demon on 2010-01-19
Are DBUS and HAL installed? There is a known issue (well, kinda) in X that says it uses Hal (which uses DBUS) to find KB/Mouse. So do a ```
su -c'pacman -S hal dbus'
``` and make sure that in the DAEMONS array in /etc/rc.conf that dbus and hal are listed (in THAT order, and preferrably in the first half of the listing, after syslog and the basic system start up.). If you're not sure, check the [wiki]("http://wiki.archlinux.org/").....

> P.s. I have to use iwconfig to manually connect to wifi... Is there a way to run these commands on startup?
Add these commands to /etc/rc.local, they will be executed last in the boot order (which is OK)

---

### Post by bodhi.zazen on 2010-01-19
> **darkeye123 said:**
> Hey everyone.

I just installed arch Linux on my pc. it wasn't nearly as hard to install as I thought it would be, and I am able to connect to my wireless now. 

However I am having some issues regarding xorg... Namely that my mouse and keyboard do not work as soon as I use xinit. 

I tried this in both lxde and plain x,but to no avail. 

I have setup x using x -configure, and copied the file into x11.

I know this is an ubuntu forum, but I wanted to ask here, since you guys have never let me down.

What should I do?

What hardware ? videocard ?

> P.s. I have to use iwconfig to manually connect to wifi... Is there a way to run these commands on startup?

You can either run those iwconfig commands in /etc/rc.local or install a gui manager such as network manager or wicd. If you are not running gnome, I suggest wicd as it will make it much easier when you are roaming on other wireless access points.

yes, it can be done with iwconfig, and wicd is the lazy way, but it is nice.

---

### Post by darkeye123 on 2010-01-19
Thank you both very much. Answer 1 worked for me :)

---

### Post by Speed Demon on 2010-01-19
> **darkeye123 said:**
> Thank you both very much. Answer 1 worked for me :)

Glad I could help... that's why I'm here.

---

