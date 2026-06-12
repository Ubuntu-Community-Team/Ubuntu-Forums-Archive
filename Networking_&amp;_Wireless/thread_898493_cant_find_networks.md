---
title: "cant find networks"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by klambert on 2008-08-23
You guys will have to excuse me, i am a complete noob at linux.  I've been wanting to switch to it for a long time (about 4 years) and the opportunity arrived when my roommate got fed up with windows so i told him i would put linux on his computer for him and play around with it (mainly for my benefit, but he gets a good working machine out of it :) ).  so anyway this is my first time, i did all the research and chose ubuntu and all that, and i installed it, runs good, didnt have any problems until i tried connecting to the internet.  It will not let me connect to a network at all, i have 3 unprotected networks around me and then mine which is protected, and the darn thing will not even pick them up.  I have read through all the guides in the help that came with it, i've tried everything that i know to do on my own, so i came to you guys.  I also do not know what kind of system information you need, like what kind of hardware and all that, just let me know what to tell yall, i'm excited to finally get a linux copy up and running.

---

### Post by pfdevil on 2008-08-23
Hey, run in the terminal lspci and search for your wireless card in the entries. If not found do a search in google to install your wireless card in ubuntu.

---

### Post by klambert on 2008-08-23
thanks man, that at least gives me a place to start, ive been at this for like 5 hours now reading trying to troubleshoot it myself and i'm just not as savy with this stuff anymore like i used to be

---

### Post by klambert on 2008-08-23
ok it is telling me that i my ethernet controller is broadcom corporation BCM4401-B0 100Base-TX (rev 02) and that my network controller is Broadcom Corporation BCM4318 [AirFore One 54g] 802.11g Wireless LAN Controller (rev 02)...does that mean that it is installed or did i not do the right thing?

---

### Post by pfdevil on 2008-08-23
What I want you to do is open a package manager eg Synaptic, Adept .etc. Do a search for ndiswrapper, three packages should come up. Install all 3, then if you still can't see any wireless networks post again.

---

### Post by klambert on 2008-08-23
the little wireless icon is up in the top corner, but thats it, i dont have a list of networks to look at or anyhting like that, the wired works fine, i finally brought everything downstairs to my router so that i can get on the internet on that comp, so the wired works, just the wireless doesnt seem to want to.

---

### Post by pfdevil on 2008-08-23
check my previous post I edited it.

---

### Post by klambert on 2008-08-23
no ndiswrapper packages, i was trying to get that ndiswrapper thing working by downloading and installing it, could that be the reason?

EDIT: ok i used synaptic package manager, and searched for it and under all it popped up, and i clicked the reload thing by accident and it started downloading package information which is 42 files...is this good/bad/right/wrong.  you will have to excuse me i am completely new to linux...i just hated windows sooo much :)

EDIT 2: hehe ok found the 3, not really understanding howto install but ill work on it and repost if i need help, thanks man

---

### Post by pfdevil on 2008-08-23
Hey don't worry about the reload part. It just updated all your respositories info. Basically in Ubuntu you install programs via the repositories, deb packages. In synaptic to install it you select the package then click apply changes. This then installs the package.

---

### Post by klambert on 2008-08-23
thanks for all your help man that did the trick...and it runs like a champ now

---

### Post by pfdevil on 2008-08-23
> **klambert said:**
> thanks for all your help man that did the trick...and it runs like a champ now

It's a pleasure.

---

