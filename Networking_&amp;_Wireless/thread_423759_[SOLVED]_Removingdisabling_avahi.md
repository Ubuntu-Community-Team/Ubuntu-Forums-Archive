---
title: "[SOLVED] Removing/disabling avahi"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by tjansson on 2007-04-26
I have a Thinkpad X30 with with built-in wireless which have work more less flawlessly for the past years. With the introduction of this annoying avahi/zero-conf thing I have started to get problems.

When the computer boots up there is no problem finding wireless accespoints but after trying to connect to such a accespoint and failing this avahi daemon takes over a gives me some random ip-address. After this I a not able to see any accespoints anymore with
```

iwlist scanning

```

I would like wipe my installation for this crappy avahi and networkmanager and do it by hand. But when I try to remove **avahi-autoipd** and **avahi-daemon** aptitude want's me to remove kubuntu-desktop. 

So my question is - how do I get rid of avahi the best way?

---

### Post by tjansson on 2007-04-26
I found a way to kille the avahi-autoip but it keeps restarting, so I guess there must be a more general way to stop it. The way to stop it for a short while:
```

avahi-autoip --kill eth1

```

---

### Post by tjansson on 2007-04-26
Found this post -http://ubuntuforums.org/showthread.php?t=417833&page=2 a

So I removed avahi-daemon avahi-autoipd network-manager and knetworkmanager

And wrote the correct information in /etc/network/nterfaces
```

iface eth1 inet dhcp
pre-up iwconfig eth1 essid "MyRouterName"
pre-up iwconfig eth1 key "MyKeyInHex"
pre-up iwconfig eth1 mode Managed
auto eth1

```

Furthermore I removed the avahi-daemon and avahi-autoipd files from /etc/network/if-up.d and /etc/network/if-down.d folders and now eveything works again. :D

---

### Post by Yoeri on 2007-04-26
What was your initial problem, maybe this can help me ...

My wireless network always worked with edgy but stopped working when upgraded to Feisty... I can see wireless networks but I cannot connect. The manual configuration doesn't work either.

---

### Post by tjansson on 2007-04-26
In my case I just found this knetwork-manager really annoying and the later found out that avahi-autopid was giving my strange problems. So with this solution I got rid of those and did by hand and now everything works as it should. :D

I don't know if the problems is the same as yours since I was able to get online with knetworkmanager a certain times. So it was not totally broken but buggy and bloody annoying. :D

---

### Post by Yoeri on 2007-04-26
I can always try ... before downgrading back to edgy

---

### Post by bernied on 2007-04-26
Just for information, removal of kubuntu-desktop doesn't actually remove anything. This package is only a bunch of dependencies, including your beloved avahi, that get the kubuntu desktop experience installed, and also keep it up to date. So that, if in the future, the kubuntu devs think that a certain application should really be part of kubuntu, they just add it to the list of dependencies in kubuntu-desktop. When you update, you get this dependency as well.

The point is that you can safely remove kubuntu-desktop, nothing will happen, except that you will now have a non-standard install. Someone tell me if I'm wrong here.

---

### Post by tjansson on 2007-04-26
That was my understanding as well - that kubuntu-desktop is just a meta package. This maybe not the best solution however - but at the moment I am very happy. :D

---

