---
title: "Intel Corporation PRO/Wireless 4965 AG or AGN"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by RichardBH on 2008-11-03
Hi,

I've just upgraded to Kubuntu 8.10, and I can no longer see any wireless networks in KNetworkManager. The wireless light on the laptop (an Acer 5920G) is unlit, and I cannot get it to switch on.

Under Hardy the light was lit the whole time and I had to do some tweaks to get it to switch on and off properly - this seems to be the opposite problem.

However, the commands I used lastime involving installing linux-hardy-backports don't work, for obvious reasons. Looking on the Intel drivers site it says that the iwlwifi driver should come bundled with this kernel, but I cant modprobe it and I can't install it (package not found).

Has anybody else had this problem and managed to solve it?

Regards,
Richard Hall

Note: This is a fresh install of intrepid, as the dist-upgrade left me with a very slow version of the KDE4.1 desktop, which locked up for 2 seconds on very click and was missing various plasma icons and things.

---

### Post by Threedays on 2008-11-03
Same.  No detection of signals at all.  I'm thinking it maybe a power-saving problem.

---

### Post by Dougie187 on 2008-11-03
Have you installed linux-backports-modules?

---

### Post by Arabiest on 2008-11-03
same here...thank u gents

---

### Post by RichardBH on 2008-11-03
Hi, thanks for the suggestion, Dougie187.

I can confirm that as far as I know, installing the linux-backports-modules-intrepid package and rebooting was what solved the problem for me.

Regards,
Richard Hall

---

### Post by teonghan on 2008-12-12
been trying to get my wireless working. i'm using acer 5920g. tried upgrading from 8.04 to 8.10 as well as fresh installation but failed. problem solved after installing linux-backports-modules-intrepid package. thanks everyone!

---

### Post by chkhurum on 2009-09-27
I upgraded to 9.04 yesterday to find out that wireless is not working. I have the same Intel Corporation PRO/Wireless 4965 AG or AGN on my laptop. Installed latest backports modules 2.6.28-15 but still does not connect to wireless network. It does not detect any network. 

Do I need to install all backports modules?

---

