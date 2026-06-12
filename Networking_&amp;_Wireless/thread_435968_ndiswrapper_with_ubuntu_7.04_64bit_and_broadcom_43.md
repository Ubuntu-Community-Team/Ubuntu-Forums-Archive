---
title: "ndiswrapper with ubuntu 7.04 64bit and broadcom 4312"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by geo_saleh on 2007-05-07
I can't get ndiswrapper work with my laptop hp dv6248eu

the wireless card is broadcom 4312

I  run these commands

```
ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 

sudo ndiswrapper -m
modprobe config already contains alias directive

sudo modprobe ndiswrapper
```

last command when I run it I got nothing

???

---

### Post by geo_saleh on 2007-05-09
up


up



up

---

### Post by Kobalt on 2007-05-09
Your last command shouldn't return anything, it's normal. After this run ```
sudo /etc/init.dnetworking restart
```
You should now be able to configure your connection from the Network-Manager applet in your notification area.

---

### Post by geo_saleh on 2007-05-09
> :~$ sudo /etc/init.dnetworking restart
sudo: /etc/init.dnetworking: command not found

what to do

---

### Post by abray on 2007-06-08
Did you ever get this working?  I have the same setup with the same card and get an occasional OOPs when loading.  Have you hit this?  If not, can you provide the steps and driver you used with NDISWRAPPER??

---

### Post by Krpano on 2008-05-02
> **geo_saleh said:**
> what to do

i think he meant:

sudo /etc/init.d/networking restart

anyway im in a hell with my 4312 rev2 here too...im almost giving it up.
I think we will have to wait till the next kernel update

---

