---
title: "wireless works on 7.10 but not on 8.04"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by ene_dene on 2008-04-28
I really don't understand it. You don't change things that work perfectly (without any configuration). On Ubuntu 7.10 wireless card worked perfectly. Now, I can see the card in system->administration->network (roaming mode enabled). Everything looks fine, but now I see my network at 0%, before I had full a signal.

---

### Post by ene_dene on 2008-04-29
I've got Asus Laptop f3jc series - ap225.
So let me explain it again. I can see a network, which used to have 100% (on Ubuntu 7.10), now the same network (2m away) has 0%. What is the problem?

---

### Post by thepisu on 2008-04-29
Same problem here, with a ASUS PCI card WL-138G V2... Are you using a "b43" driver? The new "b43" drivers seems to really have problems, but I tried I was not able to use bcm43xx drivers on new kernel...

---

### Post by ene_dene on 2008-04-29
> **thepisu said:**
> Same problem here, with a ASUS PCI card WL-138G V2... Are you using a "b43" driver? The new "b43" drivers seems to really have problems, but I tried I was not able to use bcm43xx drivers on new kernel...
I don't know about the driver. On Ubuntu 7.10 it just worked on install, if there was a wireless network it connected. On new version of Ubuntu 8.04, I can see the wireless card in system->administrator->network, and I can see my home network, but it's on 0% when I connect.

---

### Post by burunji on 2008-04-29
Hi I am having same problem.
 if i find solution i wll let you know

---

### Post by Redls1bird on 2008-04-29
I am having the same problem with 8.04 and a linksys wpc11 ver. 4.  i can see my network in wireless assistant, but cant connect.  Im not sure how to tell if my system "sees" my wireless card.

---

### Post by tmada on 2008-04-29
I am too trying to get my  ASUS PCI card WL-138G V2 to work. I have tried numerous different methods. Hopefully I can figure this out soon...

---

### Post by ene_dene on 2008-04-29
Could it be that this is some kind of a bug since the same card worked perfectly on 7.10?

---

### Post by imaworrier on 2008-04-29
Having almost the same problem as well. Everything looks fine yet cannot detect any networks at all. I am also using the broadcom 43 driver.

---

### Post by corneel on 2008-04-29
Let we call 8.04 Bugbuntu (Long Time ****)

---

### Post by TrueDego on 2008-04-29
Check out this [Blog]("http://300lb.blogspot.com/2008/04/how-to-get-broadcom-wireless-to-work-in.html").  It worked for me.  All you need is the 8.04 CD and everything works fine.  Hope this helps.

---

### Post by ene_dene on 2008-05-02
Unfortunately I had to go back to 7.10 everything works fine there. I'm afraid to think how many users that wanted to try Linux for first time got discouraged after similar problem... Things that worked in previous version just have to work fine without any advanced configuration on newer versions of system.

---

### Post by ene_dene on 2008-05-02
Here is what seems to be the problem. I've installed Ubuntu 7.10 and now I see that wireless uses Intel(R) PRO/Wireless 3945 Network Connection driver for LInux, a restricted driver. On 8.04 there is no such driver installed under restricted drivers. But still I don't know how would I put it there and use that driver that works?

---

