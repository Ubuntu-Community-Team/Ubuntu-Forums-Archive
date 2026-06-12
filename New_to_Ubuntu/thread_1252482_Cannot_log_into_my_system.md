---
title: "Cannot log into my system"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Linux Lover on 2009-08-28
I am using kubuntu 9.04. While I was updating my system, sudden power surge restarted my system and from then, I cannot log into my system.

My system is a dual boot of WinXP and Kubuntu. I can log into Win. When I am trying to log into my Kubuntu (the system I use to connect Internet) my system is delivering the option to give user name and password. As soon as I am giving user name and password, it stops working and not reaching the desktop interface.

While it stops working, if I press the mouse key, it reports an XServer error and recommends reinstalling. Is there any solution without reinstalling the system?

---

### Post by abn91c on 2009-08-28
try going to the command prompt then 
[B]sudo apt-get update
sudo apt-get upgrade[/B]
you may need to run sudo **[COLOR="Red"]dpkg --configure -a[/COLOR]** first

---

