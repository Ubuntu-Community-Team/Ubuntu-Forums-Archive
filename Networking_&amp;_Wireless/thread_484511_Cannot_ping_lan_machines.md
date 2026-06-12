---
title: "Cannot ping lan machines"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by dvlchd3 on 2007-06-25
I have a desktop and laptop running Kubuntu feisty.  There are many times that I need to copy data between the two using secure copy.  I have realized that my laptop (connected through a wireless router) after a period of time, cannot ping any machine within our lan.  I can ping any website like google, however, any 192.168.*.* machine will return unreachable.

This is weird because I cannot ping the gateway/DNS/router/server that allows it to connect out to the internet.  Does anyone know of this problem and a potential way to fix it?  I'm kinda getting tired of having to restart my machine everytime it occurs.

Thanks in advance
DAN

---

### Post by kevdog on 2007-06-25
Sounds to me like your wireless connection is crapping out??
Although this should get you reconnected is does nothing to fix the problem:
sudo /etc/init.d/networking restart

---

### Post by dvlchd3 on 2007-06-25
> **kevdog said:**
> Sounds to me like your wireless connection is crapping out??
Although this should get you reconnected is does nothing to fix the problem:
sudo /etc/init.d/networking restart

If that were the case, how come I can still view websites and ping anything outside the lan?

---

### Post by kevdog on 2007-06-25
Good point :(

---

### Post by waylow on 2007-06-26
I don't know much about routers (yet :) )
I am having almost the same issue
except I cannot connect to the internet either

I havn't got a solution yet but here is what I do to get it working again - quicker than /etc/init.d/networking restart

open up 2 terminals - ping the router in one - it will say it can't be reached

in the other
```

sudo ifdown wlan0

```
then 
```

sudo ifup wlan0

```

or in one command sudo ifdown wlan0;sudo ifup wlan0

you should see the other terminal change 

I will see how I go with a perminant solution but this will get it up and working (hopefully)

---

### Post by waylow on 2007-07-13
I think I found a solution to my problem (hopefully it helps you too)

I was using the ndiswrapper
i removed it and used the fwcutter

according to here
[https://help.ubuntu.com/community/Wi...bcm43xx/Feisty](https://help.ubuntu.com/community/Wi...bcm43xx/Feisty)

I haven't had any issues so far

i don't know what card or driver you are using but maybe this helps you solve your issue?

---

