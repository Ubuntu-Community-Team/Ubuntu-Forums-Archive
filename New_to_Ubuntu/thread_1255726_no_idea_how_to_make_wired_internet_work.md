---
title: "no idea how to make wired internet work"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by BlueCatapilla on 2009-09-01
hey everyone thanks for help, laptop with ubuntu 9.04 was given to me and i know nothing!
 
im trying to connect to a cable modem i just got from T.W.C., and i cannot find any system -> administration -> network, only network tools. 

Also, as with some other stuff ive read, under network manager under the wired networks list, it is all grayed out and there is nothing to connect. 

i also have no idea how to find out if im 
DHCP or something else or 
static IP address or what have you, 
or WPA or WEP 

i know nothing of that stuff, dont even know how to find my ip address. 

so if anyone who knows what i am supposed to do i would LOVE THE HELP!! its been killing me for the past 2 weeks >_< 
thanks!

---

### Post by st33med on 2009-09-01
Well, first off, did you connect the computer to the modem by Ethernet cable and turned the modem on? Basic step, sometimes I miss it. :)

---

### Post by BlueCatapilla on 2009-09-01
haha yeah, i have the internet part working, i also have a windows laptop that the internet wors on that im using now, just this one sucks and is slow (the comp) so i want internet to work on the other one that it doesnt with ubuntu on it :D

---

### Post by st33med on 2009-09-01
What Ethernet card are you using? To find out:

```
lspci | grep Ethernet
```

In the terminal and post it here.

---

### Post by BlueCatapilla on 2009-09-01
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 01)

---

### Post by st33med on 2009-09-01
Try:
```
sudo modprobe bnx2
```

And try Network Manager again.  If it does work, come back and tell us because there is an extra step that will need to be done.

---

### Post by BlueCatapilla on 2009-09-01
nothing....

---

### Post by BlueCatapilla on 2009-09-01
when i plug it in and look at network manager, it doesnt show anything but the wireless networks in the area, nothing under wired

---

### Post by st33med on 2009-09-01
OK, try:
```
sudo modprobe tg3
```
And check again.

---

### Post by BlueCatapilla on 2009-09-01
also nothing... :\ sry for late response, cat jumped on power plug n killed the comp -_-

****** cats

---

### Post by st33med on 2009-09-01
Doh! I forgot to tell you to unload the first module :roll:

```
sudo rmmod bnx2 tg3
sudo modprobe tg3

```

If that still does not work:
```
ifconfig
```
and post it here.

Also, cats + computers = chaos :)

---

### Post by st33med on 2009-09-01
Another thing to check:
```
lspci -k | grep Network -A 3
```

Post that here as well.

---

