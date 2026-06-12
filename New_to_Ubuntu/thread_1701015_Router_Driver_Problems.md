---
title: "Router Driver Problems"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Mely on 2011-03-05
Hi,
My name is Melissa.

I took my comp to fix and they installed this new system called ubuntu its awesome but i have a problem and no one knows what to do. I have this router and the disk for the routers drivers but i cant install it. I don't know what to do i cant use internet on my laptop unseal i intall those drivers what do i do? 

Thank You in Advance :P
:KS

---

### Post by GWBouge on 2011-03-05
I'm not sure if I can help, but I have a few questions, which might help others assist you:

1)  Home routers don't typically need drivers ... do you mean the drivers for the wireless device in your laptop?

2)  Have you tried plugging the laptop into the router directly with an ethernet cable?

3)  What brand of router/wireless device are you using?

---

### Post by Mely on 2011-03-05
Sorry its not a router its a Modem form a telephone company here in Puerto Rico, its kinda old, when they gave it to me they said i needed to install the disk they gave me. B'cause it had the drivers and programs and stuff needed for the comp to have internet. I dont know anything about comp but i installed the cabble i have always installed to the comp and no internet and i put the disc on the comp and notthing. It does not install anything.

---

### Post by seawolf167 on 2011-03-05
Welcome to the forums!

Routers don't need drivers - the cd that comes with a new router is an in-between to help you set up the settings like wireless security, etc.

The way to access your routers configuration page to set it up is to physically plug it in with an ethernet cable (from the router to your laptop), then find out what it's default IP address is.

After you plug it in to your computer, you can find it's IP address by opening a terminal (Applications -> Accessories -> Terminal), and typing the following command

```
route
```

You'll get an output thats something like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
**default         *192.168.0.1*     0.0.0.0         UG    0      0        0 eth1**
```

The part you are looking for is the "Gateway" column for the "default" row.

If you enter this into the address bar in Firefox you'll be able to setup your router.

In the above case, you'd enter

```
http://192.168.0.1
```

into Firefox's address bar, hit enter, and you'll have access to the config page. (your numbers will probably be different - maybe like 192.168.1.0 or 10.1.10.1)

---

### Post by Mely on 2011-03-05
Sorry i dont know anything about computers and like i said above its not a router its an Modem from a telephone company here In Puerto Rico could u explain in simpler words >< Thank You > **seawolf167 said:**
> Welcome to the forums!
 
Routers don't need drivers - the cd that comes with a new router is an in-between to help you set up the settings like wireless security, etc.
 
The way to access your routers configuration page to set it up is to physically plug it in with an ethernet cable (from the router to your laptop), then find out what it's default IP address is.
 
After you plug it in to your computer, you can find it's IP address by opening a terminal (Applications -> Accessories -> Terminal), and typing the following command
 
```
route
```
 
You'll get an output thats something like this:
 
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
**default         *192.168.0.1*     0.0.0.0         UG    0      0        0 eth1**
```
 
The part you are looking for is the "Gateway" column for the "default" row.
 
If you enter this into the address bar in Firefox you'll be able to setup your router.
 
In the above case, you'd enter
 
```
http://192.168.0.1
```
 
into Firefox's address bar, hit enter, and you'll have access to the config page. (your numbers will probably be different - maybe like 192.168.1.0 or 10.1.10.1)

---

### Post by seawolf167 on 2011-03-05
I didn't see your reply before I posted mine - is it a modem in the traditional sense that you'll need to "dial in" (i.e. 56k modem) to receive your internet connection? or is the internet connection always on, and you just need the modem to "talk to" your ISP?

---

### Post by Mely on 2011-03-05
> **seawolf167 said:**
> I didn't see your reply before I posted mine - is it a modem in the traditional sense that you'll need to "dial in" (i.e. 56k modem) to receive your internet connection? or is the internet connection always on, and you just need the modem to "talk to" your ISP?
 
when i had Windows XP and Vista i always had to install the disk and the stuff it comes with for the comp to umm "comunicate" with the moden and then i get internet. 
 
i never had to do any of this usualy i pay some one to do this stuff but no one knows how to work with ubuntu ppl instale it and normaly everything works they say but my modem is old doesnt have wireles and needs those programs to run 
 
Disk cover says  6381-A3 Router, User's Guide USB Drivers, PARADYNE

---

### Post by seawolf167 on 2011-03-05
> **Mely said:**
> 6381-A3 Router, User's Guide USB Drivers, PARADYNE

Your router's manual can be downloaded in pdf format from [here]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBQQFjAA&url=http%3A%2F%2Fwww.zhone.com%2Fsupport%2Fmanuals%2Fdocs%2F63%2F6381-A2-GB23-10.pdf&rct=j&q=6381-A3%20Router&ei=lgdzTbuQH8G78gaGv-GvCQ&usg=AFQjCNH4Z2kZ7sGzXJxpq6VbByjFG2INXw&cad=rja").

It looks like you can just browse to the router's default gateway which is listed in the manual as 192.168.1.1

So, plug in your router via the LAN port on the back, open Firefox (or any web browser), then in the address bar, type

```
http://192.168.1.1
```hit enter, and you'll be able to set up all the features of your router.

---

### Post by Mely on 2011-03-05
> **seawolf167 said:**
> Your router's manual can be downloaded in pdf format from [here]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBQQFjAA&url=http%3A%2F%2Fwww.zhone.com%2Fsupport%2Fmanuals%2Fdocs%2F63%2F6381-A2-GB23-10.pdf&rct=j&q=6381-A3%20Router&ei=lgdzTbuQH8G78gaGv-GvCQ&usg=AFQjCNH4Z2kZ7sGzXJxpq6VbByjFG2INXw&cad=rja").
 
It looks like you can just browse to the router's default gateway which is listed in the manual as 192.168.1.1
 
So, plug in your router via the LAN port on the back, open Firefox (or any web browser), then in the address bar, type
 
```
http://192.168.1.1
```hit enter, and you'll be able to set up all the features of your router.
 
Thank You ill go home and try it out  if it doesnt work ill be back tomorow if it does ill log in at home and thank you for ur help
 
and again thanks in advance :P

---

