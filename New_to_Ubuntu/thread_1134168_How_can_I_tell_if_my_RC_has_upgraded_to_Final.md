---
title: "How can I tell if my RC has upgraded to Final?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by agreenbhm on 2009-04-23
Hi everyone!

I installed 9.04 Netbook Remix RC on my netbook last weekend.  I have been updating everything every few days, and today, when I went to upgrade to the final release or 9.04, there were only like 4 packages to update, mostly pertaining to FireFox.  How can I tell if I have the actual Jaunty Final or still just RC?

Thanks,

Drew Green

---

### Post by Nepherte on 2009-04-23
Your mirror has probably not been synchronized yet.

---

### Post by drs305 on 2009-04-23
System, Administration, System Monitor: System. It will state "Release 9.04 (jaunty)"

---

### Post by lukjad on 2009-04-23
I'm not absolutely sure, but from what I heard, the RC and the actual release are so alike, it's only a matter of a few updates. In fact, I was told that they ISO's are basically are the same. So, if you get any updates, you probably are in the "full" version. :D

---

### Post by drjonze on 2009-04-23
> **lukjad007 said:**
> I'm not absolutely sure, but from what I heard, the RC and the actual release are so alike, it's only a matter of a few updates. In fact, I was told that they ISO's are basically are the same. So, if you get any updates, you probably are in the "full" version. :D


I think this is true. I've been running the beta since it came out. There were lots of updates at first, but then they slowed down and today, there were only a few. I tried to upgrade using the alternate CD and it said I was already running the latest version. My GRUB options changed from 'Ubuntu Jaunty Development Branch...." (or something like that) to "Ubuntu 9.04, ....". It looks like I have the final release. But its a moot point anyway as I just did a fresh install. I have my /home on its own partition and I just save my packages list, it makes installs so much easier (if you're going from same version to same version). 

When the beta came out, I just did an upgrade (from 8.10), got everything working and then saved my packages (Synaptic-Save Marking As...), that way, I'd have all the packages for jaunty so I could just re-install all my extras en masse. Then I did a fresh install of the beta and had no issues.  It was also a good opportunity to see exactly what I had and get rid of some of stuff I installed but never really used.

---

### Post by LowSky on 2009-04-23
just run 

```
sudo apt-get update & sudo apt--get upgrade
```

and all will be up to date

---

### Post by Paqman on 2009-04-23
> **drjonze said:**
> My GRUB options changed from 'Ubuntu Jaunty Development Branch...." (or something like that) to "Ubuntu 9.04, ....". 

I always really like it when this happens. It's the most obvious sign that you've gone from the testing branch to the stable release. It's like coming to the end of a journey :)

---

### Post by lukjad on 2009-04-23
Now, when will they change it one the forums. ;)

As I sit here, I see "**Ubuntu Jaunty Jackalope (testing)**" still...

---

### Post by tony_clifton on 2009-04-23
> **agreenbhm said:**
> I installed 9.04 Netbook Remix RC on my netbook last weekend.  I have been updating everything every few days, and today, when I went to upgrade to the final release or 9.04, there were only like 4 packages to update, mostly pertaining to FireFox.  How can I tell if I have the actual Jaunty Final or still just RC?

I saw the exact same thing going from RC to the final release.  Got the RC a week ago, everything worked fine, only a few updates since then, beat the rush, EXT4 rocks, life is good.  :)

---

### Post by mamamia88 on 2009-04-23
stil says testing branch here

---

### Post by bthodla on 2009-04-24
I found this on [http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-ibex-to-ubuntu-904-jaunty-jackalope-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-810-intrepid-ibex-to-ubuntu-904-jaunty-jackalope-beta.html).

From the terminal, type:

sudo lsb_release -a

When I do this on my machine, I get:
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

Looks like mine has been upgraded to the actual release.

---

