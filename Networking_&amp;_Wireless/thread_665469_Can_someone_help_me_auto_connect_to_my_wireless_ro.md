---
title: "Can someone help me auto connect to my wireless router?"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by joesmith1234 on 2008-01-12
here's my /etc/network/interfaces file...

```

auto lo
iface lo inet loopback

#code added by joe
auto ath0
iface ath0 inet dhcp
wireless-essid SamAdams
wireless-key aaf10bb0cd4aeaba331245632145

```

And yes, that's not my wireless key ;) but I just wanted to show explicitly that I'm entering a hex value.

So should this work?  I don't get any error messages when I log out and log back in...
But my network manager doesn't show any connection and firefox won't connect to anything.

However, I can connect if I use the network manager to connect to my network.

Also FYI, this is a fresh reinstall of XUbuntu Gutsy.

---

### Post by joesmith1234 on 2008-01-12
More info:
I'm not actually sure if I should be using ath0 or something else.

---

### Post by joesmith1234 on 2008-01-12
> **joesmith1234 said:**
> More info:
I'm not actually sure if I should be using ath0 or something else.

Ok, when I log in the GUI way, the ethernet "thing" is wlan0, so I change ath0 to wlan0 in the above, but there's still nothing happening.  

Hm.

---

### Post by joesmith1234 on 2008-01-12
ok, I got it to log in with "sudo ifup wlan0"...

i'm going to start another thread for related questions i guess

---

### Post by ubutufan on 2008-01-12
Just leave the first two lines in the /etc/network/interfaces file as they are

Comment out all the rest. All of them

---

### Post by elj4176 on 2008-01-14
im having a similar problem on an old dell running a fresk copy of xubunto 7.10.

sudo iwlist scan

shows my wireless network and my neighbors on ath0

ive taken the working inyerfaces wep config from this laptop to connect to my network but I cannot ping anything.
if i can see networks with iwlist then I should be able to connect right?
any help? 

The old dell doesnt even have an ethernet port on it! P3 that had win98 on it.

---

