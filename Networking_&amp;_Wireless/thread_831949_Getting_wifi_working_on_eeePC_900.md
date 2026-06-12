---
title: "Getting wifi working on eeePC 900"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by Moezzie on 2008-06-17
I just got my shiny new black eeepc 900 a couple of days ago. The default xandros dist did not survive for more than a couple of hours. I replaced it with [[COLOR="Red"]Ubuntu eee[/COLOR]]("http://www.ubuntu-eee.com/index.php5?title=Main_Page") which works really well. Wifi works almost flawslessly out of the box and most of the other stuff is fixed by following the guides on the page. 

Anyways, my wifi did always stop working after every reboot. I found that restarting all networking interfaces would enable the wifi again.

So i simply added this line to my /etc/rc.local :
```
/etc/init.d/networking restart
```
This restarts all your networking interfaces every time you start your computer. 
To be honest, i have no idea what happens behind the scenes of this. I know there alot of problems with the wifi on the eeepc still, so i hope this might help some of you.

---

