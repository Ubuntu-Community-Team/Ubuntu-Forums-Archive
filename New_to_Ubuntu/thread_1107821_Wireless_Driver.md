---
title: "Wireless Driver ?"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-03-27
Hi I am back. I have a quick question... I am using Mandriva right now but want to go back to my Ubuntu... Mandriva is using a rausb0 driver but when I try Ubuntu it uses a rt2500usb driver. How can I change this driver to the rausb0 driver? Thanx...

---

### Post by stderr on 2009-03-27
Hi Leo,

Uhm, I believe rausb0 is what the driver that Mandriva was using named the connection. For example, most people's ethernet connections on linux get named eth0 or eth1, and many wireless connections get called wlan0, wmaster0, and (so I believe) rausb0 for some reason. 

In contrast, rt2500usb is an actual driver, and I would imagine rt2500usb is actually the name of the driver's kernel module. 

I would presume Mandriva is quite likely using the same driver as Ubuntu is? When in Mandriva, if you do a:

```
lsmod | grep rt2500
```

do you get any response? Either way, running this in mandriva (if it's got this package) should determine the driver your network card's using:

```
lshw -C network | grep driver
```

e.g. mine returns:

```
WARNING: you should run this program as super-user.
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.69 latency=0 module=**r8169** multicast=yes
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

indicating I'm using the r8169 driver. Running lsmod confirms it:

```
lsmod | grep r8169
r8169                  36100  0 
mii                    13440  1 r8169
```

So, I'm not quite sure what you really want to do...

---

