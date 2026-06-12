---
title: "weird network behaviour when updating - hangs router"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by rniella on 2007-08-04
Hi, I have an AM D2.8GHz 1GB RAM and using Ubuntu Dapper for about a year now.  I`ve upgraded my dsl conecction to 1 Mbps (from 256)  about a month ago and since then, every time I run a system update it hangs my Linksys routerBEFW11S4.  The weird part is that the internet works great otherwise, I download tons of stuff, use p2p, FTP, etc and most of the time i see transfer rates close to 100 KBps (bytes), which is close to 1 Mbps.. any how, any time I run the system update, or the apt-get update (on a terminal), the connection goes well for a few seconds, then the trasfer rates drop to 3 Kbps and the to nothing, when I need to turn off-on my little router...  Any ideas why might this be happening ???  thanks a lot !

---

### Post by noob12 on 2007-08-04
My guess is this is not your router but a bad repository in /etc/apt/sources.list (or the parts in /etc/apt/sources.list.d), or you happen to be getting redirected to a bad mirror site on one of the redirectors.

I don't know how to get apt or apt-get to log actual sites that you are going to.  Maybe someone else here does.

In lieu of that, while running apt-get in one window, I would run a trace in another window using  ```
sudo tcpdump -i eth0 tcp port 80 and host *your.ip.address* 
```.

This assumes eth0 is your interface and *your.ip.address* is the address currently assigned to that interface; **ifconfig** will tell you these values (or me if you post the output).

---

### Post by rniella on 2007-08-05
Hi noob12, thanks for your help.  I did that now and I`m attaching the log (or what I could copy-paste from the terminal window).  The extrange thing is that this time it worked !!  I could update my system no problem at full speed !!  I`ll use your method next time I run into problem ... thanks for now !

---

### Post by rniella on 2007-08-05
Now it happened again.  I was trying to upgrade from dapper to Edgy and can`t get pass the first few minutes of the upgrade.. the transfer rate goes down to nothing (even whene I can still surf the web at high rates) and after that the router hangs, then I need to turn it off and then on.  I`m including the net log right up to the point where it hangs, when doing this I did not surf the web to avoid confussion on the log.  thanks in advanced !

---

### Post by rniella on 2007-08-05
Dont worry guys, I changed my DSL provider (I have a different user/paswd) and now it works like a charm.  My previous ADSL provider was somehow limiting my transfer rates as soon as it reached its maximum.. so, now it is all cleared.  Thanks !

---

