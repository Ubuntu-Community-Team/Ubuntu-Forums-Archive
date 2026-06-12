---
title: "pppoe coneection at startup"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by karellen on 2006-12-06
Hello everyone. I have a pppoe connection and I managed to set it right in ubuntu. I do sudo pppoeconf every time, I input my username and password and then everything works fine. my problem is that I don't want to do that every time I want to be connected, but my connection to be available when booting. I noticed that only my password is not remembered between two consecutives pppoeconf. I'd like to know if there is something like a graphical tool for pppoeconf, like it is for ethernet connection. It would be very helpful...

---

### Post by bilbarra on 2007-06-11
im in the same ship :(

---

### Post by Draku on 2007-06-11
You don't have to use **sudo pppoeconf** every time you boot to start your connection:
**for connect :**> sudo pon dsl-provider
**for disconnect :**> sudo poff dsl-provider

And for connect @boot use this :

> sudo gedit /etc/network/interfaces

and move the line : pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf in front of auto dsl-provider
ending with something like this:
> pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

---

### Post by bilbarra on 2007-06-11
tanks, :)
i will see if works next time i boot. 
but why they dont fix this? 
all previous releases has the same problem, pppoeconf say that wil start on startup and dont...:(

---

