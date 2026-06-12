---
title: "an update blew my xserver up..."
date: 2010-03-17
forum: New to Ubuntu
---

### Post by linux_noob0 on 2010-03-17
something's gone wrong with the last update i made. my graphics were broken as usually, but i keep the installation file nearby just in case. the problem is, i can't kill the x server normally to do the installation.

after jumping to non-graphic mode..

when i try: sudo /etc/init.d/gdm stop, or restart, it starts telling the script has been somehow converted, so i can say stop gdm ( which totally doesn't work ), or just gdm stop ( which RESTARTS my xserver, i just get the login screen )... wtf??

i can't install my graphics now cause the xserver is running all the time :/
anyone knows how to handle this? thanks!

---

### Post by undecim on 2010-03-17
What is the error message you get when you run "sudo /etc/init.d/gdm stop"?

---

### Post by linux_noob0 on 2010-03-17
it doesn't execute it, just tells me to use "gdm stop" instead...

Rather than invoking init scripts through /etc/init.d, use the service( 8 )
utility, e.g. service gdm stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop( 8 ) utility, e.g. stop gdm

---

### Post by QIII on 2010-03-17
The message may be a bit cryptic.

If you are using Karmic, what it is telling you to do is type

```
sudo service gdm stop
```

Similar commands:

```
sudo service gdm start
```

```
sudo service gdm restart
```

---

### Post by linux_noob0 on 2010-03-17
> **QIII said:**
> The message may be a bit cryptic.

If you are using Karmic, what it is telling you to do is type

```
sudo service gdm stop
```Similar commands:

```
sudo service gdm start
``````
sudo service gdm restart
```

his reply is:

stop: Unknown instance:

---

### Post by GSF1200S on 2010-03-17
I guess you could always do:
```
sudo killall Xorg
```
or
```
sudo killall X
```

You can use a system monitor, htop, or even kill pid to kill the Xserver as well.

If you have issues starting gdm after installing your vid drivers, try:
```
startx
```

You may want to reinstall gdm as well- seems you have issues there.

---

### Post by linux_noob0 on 2010-03-17
thanks, that worked... now it seems that service gdm stop works when i go into command mode too..

---

