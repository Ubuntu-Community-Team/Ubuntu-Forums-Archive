---
title: "Freeing up memory"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by fro1269 on 2009-04-14
I'm trying to free up  some memory on my Ubuntu 8.10 installation. Im running kernel  2.6.27-11-generic. I currently have 1 gig of ram installed and with just gnome desktop and firefox running I only have 64 megs free. How can I tweak my install so that I can use my system more efficiently?

---

### Post by LesterPalooza on 2009-04-14
You can reduce the number of programs at startup

System>Preferences>Sessions

or you can terminate unneeded processes by typing

ps -x or ps -A in your terminal

and typing kill -9 <process id number> to terminate the process

example:

kill -9 12034

This can free up some RAM. BE CAREFUL! DO NOT END A PROCESS THAT YOU ARE NOT FAMILIAR WITH - YOU CAN CRASH YOUR LOVEBUNTU.

---

### Post by Sef on 2009-04-15
Linux runs the ram, and when it is needed it releases it.

what does ```
free -m
``` say?

---

### Post by oldsoundguy on 2009-04-15
> **fro1269 said:**
> I'm trying to free up  some memory on my Ubuntu 8.10 installation. Im running kernel  2.6.27-11-generic. I currently have 1 gig of ram installed and with just gnome desktop and firefox running I only have 64 megs free. How can I tweak my install so that I can use my system more efficiently?

something is seriously wrong with your install or you have loaded a bunch of programs that you do not need .. also check just WHAT you have in Firefox that loads when it does .. most of the items in the add-ons do NOT need to be launched to function.
Or, it just could be you are reading your "usage program" incorrectly.
NO WAY only 64mb available from 1gb just with the kernel/desktop/browser running NO WAY!!

---

### Post by iponeverything on 2009-04-15
If the Kernel has spare memory, it will use it for caching - this is a good thing - this memory is used for other things if needed.

---

### Post by juancarlospaco on 2009-04-15
You really dont want it, makes the system faster...

---

### Post by fro1269 on 2009-04-15
> **Sef said:**
> Linux runs the ram, and when it is needed it releases it.

what does ```
free -m
``` say?

I just realized that i was totally reading the output to the free -m command wrong after I went into System monitor and saw that I actually had about 750 megs free after a restart with FF open on one tab. Upon further research it appears that firefox is what is hogging up my resources. It seems like the more I use it, the more memory it hogs up, Right now with 4 tabs open it is taking up 67 megs, the addons I have installed are Power Twitter (currently not active), Xmarks, personal menu, and adblock plus.  In about 24 hours of use it will be taking up about 130 megs. Is there any workaround to make FF more efficient?

---

