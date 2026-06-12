---
title: "Atmel driver works fine off LiveCD, fails in HD install"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by LiteWait on 2006-09-13
what a pisser...xubunutu liveCD recognized my atmel-based PCMCIA wifi card perfect, installed to hard disk now (I think) it won't load with an error like "cs: warning: no high memory available, cd: unable to map card memory!" 

dmesg (on liveCD) is:  eth0: Atnel at76c50x. Version 0.98
I just update /etc/network/interfaces and eth0 comes up perfect!


Anyone seen this before?

---

### Post by george314 on 2006-09-13
how do you "update /etc/network/interfaces"

I have a similar problem with an Inte 2915ABG wireless card.  I.E. my wireless card works with the live CD but not when I have installed Ubuntu 6.06.  So please explain how you fixed the problem.  Thanks.

George314

---

### Post by LiteWait on 2006-09-13
George,
You should be able to edit /etc/network/interfaces if your driver loads (my problem is the driver is not loading).

do iwconfig and add an entry for the interface that matches your wireless card (usually eth0 or wlan0).  There is a sample in the Wiki.

HTH, LW.

---

### Post by mepaco on 2006-09-13
Not sure if it is the same problem, but my wireless card was doing the same thing (worked on Live CD but not install). See this post for my solution:

[http://www.ubuntuforums.org/showpost.php?p=1496332&postcount=5]("http://www.ubuntuforums.org/showpost.php?p=1496332&postcount=5")

-Paco

---

### Post by LiteWait on 2006-09-14
You done good.  That was the problem.  Not sure why the LiveCD version generates that file and the HD install doesn't, but that is a problem for another day.  Thanks!

---

