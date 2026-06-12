---
title: "restarting network services"
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by lsiden on 2005-04-27
I want to change some settings in /etc/network/interfaces, then restart the network.  However, every time I enter (as root or sudo) "/etc/init.d/networking restart", despite the success message, the network is henceforth unavailable until I reboot the machine (telinit 1 is not sufficient!).  This persists even after restoring /etc/network/interfaces to it's original state.  Can anyone tell me what I may be doing wrong?

---

### Post by dave9191 on 2005-04-27
Ive had a problem that my wireless would not always work after resuming from suspend/hibernate. And restarting would fix that. But Ive managed to restart the network by 

/etc/init.d/networking stop
unloading wireless module from kernel 
loading it up again 
/etc/init.d/networking start

and that works for me. Even if you arent using wireless there must be a module for the ethernet port ( i cld be wrong tho ). And instead of restart, try stopping and starting.

---

### Post by henriquemaia on 2005-04-27
[QUOTE=lsiden]I want to change some settings in /etc/network/interfaces, then restart the network.  However, every time I enter (as root or sudo) "/etc/init.d/networking restart", despite the success message, the network is henceforth unavailable until I reboot the machine (telinit 1 is not sufficient!).  This persists even after restoring /etc/network/interfaces to it's original state.  Can anyone tell me what I may be doing wrong?[/QUOTE]

I have the same problem. Even though I have understood the instructions given above by Dave, is there no other way of accomplishing this, a simpler one?

---

### Post by siebzehn on 2005-04-27
Please post your  /etc/network/interfaces  file so we can se the config

--
Siebzehn

---

