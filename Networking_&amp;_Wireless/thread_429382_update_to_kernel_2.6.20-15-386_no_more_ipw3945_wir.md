---
title: "update to kernel 2.6.20-15-386 no more ipw3945 wireless"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by greatshape on 2007-05-01
hi,

I can't use my intell pro wireless device ipw3945 with kernel 2.6.20-15-386. 
The module seems to get loaded, but ifconfig doesn't show the interface. ifup eth1 results in no such interface.
When I boot kernel 2.6.17-10-386, everything works perfect and without any issues.
Am I the only one? Anyone has a solution for this?

Many tnx.
Steve

edit: I just notice kernel 2.6.17 uses ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
as far as i remember 2.6.20 used the 1.2.0mp driver version

---

### Post by Teamgeist on 2007-05-01
```
sudo apt-get install linux-restricted-modules-generic
```
In case you have not done that yet.

---

### Post by greatshape on 2007-05-01
> **Teamgeist said:**
> ```
sudo apt-get install linux-restricted-modules-generic
```
In case you have not done that yet.

Well, actually I already did, so I tried the generic kernel and it worked.
I noticed now there is a non-free package of ia386 restricted modules for that kernelversion too. 
```

steve@lappie:~$ sudo apt-cache search linux-restricted-modules 386
linux-restricted-modules-2.6.20-15-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-386 - Restricted Linux modules on 386.

```

I'm installing it right now and I guess it will solve the problem.
Kind regards,

Steve

EDIT: Problem solved after installing the non-free modules

---

### Post by piovisqui on 2007-05-01
I have the same problem. I've installed  linux-restricted-modules-2.6.20-15-386 and  linux-restricted-modules-2.6.20-15-generic  (and both kernel versions) and when i try to launch the daemon says that it's already lauched but iwconfig does not show the wirelesss device. :(

I remember that I installed these packages today in order to install Metisse (the nucleo did not compiled still...):
apt-get install libstroke0-dev libpng3-dev libc6-dev libreadline5-dev librplay3-dev libxmpi4-dev libxft2-dev libxrender-dev fvwm-icons libexif-dev libavformat-dev libgtk2.0-dev libcv-dev libavahi-core-dev libcoin40-dev libavahi-compat-libdnssd-dev libgl1-mesa-dev libglut3-dev vx-icons

Can it be some conflict?

How do I solve this?

---

### Post by greatshape on 2007-05-03
> **piovisqui said:**
> I have the same problem. I've installed  linux-restricted-modules-2.6.20-15-386 and  linux-restricted-modules-2.6.20-15-generic  (and both kernel versions) and when i try to launch the daemon says that it's already lauched but iwconfig does not show the wirelesss device. :(

I remember that I installed these packages today in order to install Metisse (the nucleo did not compiled still...):
apt-get install libstroke0-dev libpng3-dev libc6-dev libreadline5-dev librplay3-dev libxmpi4-dev libxft2-dev libxrender-dev fvwm-icons libexif-dev libavformat-dev libgtk2.0-dev libcv-dev libavahi-core-dev libcoin40-dev libavahi-compat-libdnssd-dev libgl1-mesa-dev libglut3-dev vx-icons

Can it be some conflict?

How do I solve this?

Hi,

You don't need the generic kernel.
Are you sure BOTH these packages are installed? 
```

linux-restricted-modules-2.6.20-15-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-386 - Restricted Linux modules on 386.

```
if not, install what's missing and try again. 

Kind regards,
Steve

---

### Post by piovisqui on 2007-05-04
First: lol o.O

Do you remember that some notebooks have a mechanical switch to turn off wireless and bluetooth? It was just switched off....

---

### Post by greatshape on 2007-05-05
> **piovisqui said:**
> First: lol o.O

Do you remember that some notebooks have a mechanical switch to turn off wireless and bluetooth? It was just switched off....

LOL :-) yeah, those things happen ....

Kind Regards,
Steve

---

