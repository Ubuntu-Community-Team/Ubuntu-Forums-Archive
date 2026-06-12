---
title: "wlan0 gone"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by lsrcnik on 2013-11-19
I have the Acer Chromebook C7 and i'm using Chrubuntu on it which is basically Ubuntu 12.04.
I moved in to this new atp. which requires me to connect to the internet using a broadband connection. Ive been looking for instructions online, and i've messed with the pppoe settings. Anyway, after i've done what the instructions said but after the reboot, ive lost the little wireless networks icon up there and now i can't use it.

```
sudo pppoeconf wlan0
3. OKAY TO MODIFY -> yes
4. POPULAR OPTIONS -> yes
5. ENTER USERNAME -> usernam
6. ENTER PASSWORD -> password
7. USE PEER DNS -> yes
8. LIMITED MSS PROBLEM -> yes
9. DONE -> yes
10. ESTABLISH A CONNECTION -> yes
11. CONNECTION INITIATED -> ok

 editi network interfaces file:
terminal: 
pico /etc/network/interfaces
1.  "iface wlan0 inet manual" to be "#iface wlan0 inet manual"
2. crtl+x -> y ->  enter
3. Reboot.
```

P.S. I've started using linux out of need, because i got this chromebook thing but i couldnt do anything with it until i found out you can put an actual OS on it. So i am a noob, and if you need more info, ask. 
what do? help.

---

### Post by praseodym on 2013-11-19
Hi,

why do you need pppoeconf? Do you have a router? If yes, add the login and password of your PPPoE connection in your router interface. Re-set the /etc/network/interfaces to
```

auto lo
iface lo inet loopback
```
Reboot and connect via networkmanager

---

### Post by lsrcnik on 2013-11-19
It was the only way to connect to the network, i'm not sure on what principle it works but right now i'm using windows and first i needed to connect to the wireless network and then make a broadband connection. Yes, i do have a router.
I'll try this right now and tell you the results. I dont want to throw my laptop in the garbage.

---

### Post by lsrcnik on 2013-11-19
Another thing, now it takes like 4 times longer to boot.

this is how it looks like now

```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider


auto wlan0
iface wlan0 inet manual
```

> **praseodym said:**
>  add the login and password of your PPPoE connection in your router interface.&#382;

> **praseodym said:**
> 
Reboot and connect via networkmanager


How exactly do i do these things? Like i said, total beginner.

---

### Post by lsrcnik on 2013-11-20
Bump. Still don't know what to do.

---

