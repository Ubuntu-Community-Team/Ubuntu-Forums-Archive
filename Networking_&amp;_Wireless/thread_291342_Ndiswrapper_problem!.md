---
title: "Ndiswrapper problem!"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by tjololo on 2006-11-02
Hi!
I have a problem width ndiswrapper on my laptop](*,) 
I have installed ndiswrapper downloaded the driver and told ndis where it is...
when i check it says driver present, hardware present, BUT my wireless card is still listed as eth1 not wlan0 as it should...
Can anyone help me? I have been looking in the forum and googling for days!:x
BTW: I have a bcm wlan card

---

### Post by somersetsimon on 2006-11-02
Are you running Edgy? I have tried genuine Linux drivers and ndis wrapped windows drivers for both Dapper and Edgy. Dapper always identifes the wireless connection as wlan0 and Edgy always identifies it as eth1. Either way, my wireless connection is always identified correctly, but I've never been able to connect or even ping my router.

---

### Post by tjololo on 2006-11-06
I'm running dapper... I found out that it doesn't matter if it is eth1 or wlan0. I got it working for about 2sec but after that it hasn't been working...:mad: ](*,)

---

### Post by Stinger on 2006-11-06
I don't know if it helps or not but here you can see how I got my ASUS WL-138G working.

[http://www.ubuntuforums.org/showthread.php?t=288341]("http://www.ubuntuforums.org/showthread.php?t=288341")

BTW. if your using ndiswrapper you should be using wlan0.
eth1 indicates edgy has a build in driver too.
Maybe you don't need ndiswrapper in edgy ?
Cheers

---

### Post by somersetsimon on 2006-11-06
I managed to overcome my ndiswrapper problems in dapper by making sure I had absolutely the latest windows driver and blacklisting all the built-in linux ones. When I did this, my wireless card worked perfectly. I haven't tried the same thing in edgy, so I don't know if that sorts out the wlan0/eth1 issue.

---

### Post by dmizer on 2006-11-06
> **somersetsimon said:**
> I managed to overcome my ndiswrapper problems in dapper by making sure I had absolutely the latest windows driver and blacklisting all the built-in linux ones. When I did this, my wireless card worked perfectly. I haven't tried the same thing in edgy, so I don't know if that sorts out the wlan0/eth1 issue.

post the output of lsmod.  we can tell what module is trying to load for your card instead of ndiswrapper, and then you can blacklist it.

```
lsmod
```

---

