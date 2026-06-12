---
title: "Atheros No wireless option"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by Ub2daUntu on 2008-04-06
Hey, I'm new to Ubuntu (currently had it installed only about 4 hours) but in that short time its been working great for me except for my wireless.

I was searching the forums for help but I'm a total noob when it comes to understanding computers. So the problem is that when i go to the network manager there is no wireless option, just wired and modem. Does anyone know how I can fix this?

I'm not totally sure what specs I should post so just tell me if you need more info.

I'm using an Acer Aspire 4720z and I'm running Ubuntu 7.10 (Feisty something i think).

Thanks in advance:)

---

### Post by DXM31 on 2008-04-06
For Atheros you need madwifi.
If you have atheros 5007eg you need
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)
or
[http://ubuntuforums.org/showthread.php?t=719863&highlight=5007](http://ubuntuforums.org/showthread.php?t=719863&highlight=5007)
Network Manager never worked for me

---

### Post by scraghty604 on 2008-04-07
Hi i am also a noob, cant stand windows anymore so thought i would see what the fuss is about...i have a acer 5570z  (5570-2094)

i guess my #1 probelm is WHAT wireless card do i have, iv googled and cant seem to find what i am looking for.

Then getting it to work is the next problem

I belvie i have the regular ubuntu, with the orange background if that makes a diffrence

I sorta get how this hole thing works but its all new to me can anyone point me in the direction of some good noob show me WTF i am doing stuff :P thanxs

---

### Post by DXM31 on 2008-04-07
I have the same laptop.
Use the second link in my post above and you will be up and running in no time

---

### Post by Ub2daUntu on 2008-04-07
I'm actually using Atheros AR5BXB63. I think...

---

### Post by DXM31 on 2008-04-07
I need to read better mine is 5570-2609
Who knew they would have different cards??
Anyway I would still go with madwifi.
Just look on their page for the how to load it.

---

### Post by kevdog on 2008-04-07
madwifi does not support all atheros cards -- you need to check the compatibility chart.  If its not on the chart I would definitely google and see what others have done.  ndiswrapper is usually a fallback.

---

