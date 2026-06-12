---
title: "wireless goes after 5 min"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by ser_virtual on 2007-12-11
I'm trying to connect to a WPA-enterprise secured wireless but I can only do at the very sesion beggining. Then, after 5 min the connections goes out and I'm not able to recover it. I'm using a broadcom wireless card with the restrictec drivers and firmware provided by the restrictec device manager in ubuntu. The network manager perfectly sees all wireless network around.

What can I do?

---

### Post by saechen on 2007-12-11
I had the same problem and had to setup using the ndiswrapper method.  

Is discussed here: [http://ubuntuforums.org/showthread.php?t=340689&highlight=broadcom+ndiswrapper](http://ubuntuforums.org/showthread.php?t=340689&highlight=broadcom+ndiswrapper)

The original post was from a while ago so I would read through it for updates.  If I find a better link will add it to the post.

---

### Post by jundalabee on 2007-12-11
I also had the same problems with older versions of ubuntu. It seems in Gutsy though, it is much more stable for my system. What version are you running?

---

### Post by kevdog on 2007-12-12
Id recommend changing from the restricted bcm43xx driver to the ndiswrapper method.  Much more stable.

---

