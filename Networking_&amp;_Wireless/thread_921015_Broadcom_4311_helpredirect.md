---
title: "Broadcom 4311 help/redirect"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by brandon88tube on 2008-09-15
I am completely new to linux and I was searching around on the forums and internet on how to fix my Broadcom 4311 rev(02) AirForce54g card so that I can connect online with my HpDv8240us laptop. I read some articles and that, but I am completely lost on how to do this and I don't have any internet on that laptop so that makes it a little more difficult. If anyone could help or redirect me to a tutorial for a complete moron to linux I would greatly appreciate it. 

Other info that you may need to know...

64-bit version of Ubuntu Hardy 8.04
Used wubi install

---

### Post by Ayuthia on 2008-09-16
If I recall correctly, the 4311 rev 02 card did not work so well with the b43 drivers in Hardy.  I want to say that it might be fixed in 8.04.1 but I am not positive on it.  If you want to try it you can try this guide:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

The other option is to try using the Broadcom driver.  It does seem to connect at better speeds and for some people it has a better range than the other two options.  The downside to this driver for Hardy is that it does not work for ssh.  I have also found out recently that this driver does not work with remotely connecting to mysql.  If you want to try this one:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

The other option is to go with NDISwrapper.  This one requires some additional configuring and needs Windows wireless drivers (not Vista though -- they are listed as bcmwl6) to make it work.  However, once you get it installed and configured, it works pretty well.  Here is the link to a guide for this one:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps.

---

### Post by brandon88tube on 2008-09-16
Thanks for the reply, I will be trying this and try to report back later if I can.

---

### Post by brandon88tube on 2008-09-16
Well I did the first step you suggested and it tries to connect, but ends up crashing my router constantly. Also I do have version 8.04.1 installed. If you could help me figure out what is wrong so that I can get linux from crashing my router that would be great :D

---

### Post by Ayuthia on 2008-09-17
> **brandon88tube said:**
> Well I did the first step you suggested and it tries to connect, but ends up crashing my router constantly. Also I do have version 8.04.1 installed. If you could help me figure out what is wrong so that I can get linux from crashing my router that would be great :D

It is crashing your router?  I have no clue about what to do with that.  When you say that, do you mean that your router locks up and you have to power it down?

You might try the ndiswrapper route(third option). It is a little more complicated, but I am guessing that it will not crash your router because it is using a Windows driver.  I could be wrong though.

---

### Post by brandon88tube on 2008-09-17
It sends my router into an endless sort of loop where the lights go all red and then it restarts itself. I have to log out of Ubuntu in order for my router to reset itself again. The router I use is a 2wire Wireless router with the three main lights on it. Not sure if that helps or not. I will try to go the other route and see what happens.

---

### Post by brandon88tube on 2008-09-17
I am now typing this from my laptop with Ubuntu on it :D The third part which you suggested with using the ndiswrapper seemed to have worked. Thanks again, now you can probably list this thread as SOLVED.

---

