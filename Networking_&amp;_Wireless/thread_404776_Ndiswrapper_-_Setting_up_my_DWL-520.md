---
title: "Ndiswrapper - Setting up my DWL-520"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Morca007 on 2007-04-08
Hi, I am trying to get my wireless card to work in Feisty, and am encountering some trouble.

I am using the version of ndiswrapper that came on the 7.04 CD, and am trying to set up my D-link DWL-520 (Rev. E1) wireless card.

What I have done so far:
Copy the XP drivers from my installation CD (NETPRISM.INF, PRISMNDS.sys)
In console:
ndiswrapper -i /home/matt/drivers/NETPRISM.INF
-Now, here I get an error telling me that it doesn't exist, and if I enter it again, it tells me that it is already installed.
ndiswrapper -l
-Tells me that netprism is installed, but is an invalid driver

What am I doing wrong?

---

### Post by josephus on 2007-04-09
Ndiswrapper is a little bit weird in this regard.  To uninstall the bad driver:

```
sudo ndiswrapper -e <drivername> 
```

Try installing it again and make sure you have the right path/name (upper/lowercase counts)

---

### Post by Morca007 on 2007-04-09
I've done that a few times. Still no change.

An interesting tidbit I picked up on the linuxquestions forum is that my card may be one that requires a firmware load. :-/

---

### Post by benjo316 on 2007-04-19
I think what you did wrong is you had .inf capitalized... I checked and on the driver CD of my card it is all capitalized except the .inf part. Hope this helps. ^.^

---

