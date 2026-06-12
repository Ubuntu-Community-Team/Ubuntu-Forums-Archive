---
title: "Linuxant driver problems"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by Winston_Smith on 2008-09-10
I've installed the Linuxant drivers provided by dell, but seem to have a problem. I've looked around but can't seem to find anything on this problem. 

What happens is the connection will drop at random, when I try to reconnect the modem is not reachable, I'm using Gnome-PPP to connect. When this happens I have to stop the driver (hsfconfig --rcstop) Then restart it (hsfconfig --rcstart) this fixes the problem untill it happens agian.

I can browse but it's annoying to have to stop and start the driver.

---

### Post by Shazaam on 2008-09-10
What do you have the speed set at in gnome-ppp setup? 57600 works for me. The only disconnects I get now are caused by my isp's usage settings (every 30 min). Their excuse is that they disconnect regularly to allow more users to connect.
Speaking of which, I have 3 local numbers that I dial into. Have you tried any other numbers?
Also, try running gnome-ppp in terminal and see if it spits out errors when you get disconnected.

---

### Post by Winston_Smith on 2008-09-10
It's not the isp or Gnome-pp, it's the driver itself. After I'm disconnected I can't even dial back in, I get a modem like the modem is not even found. I have to manually stop then restart the driver itself before I can dial back in.

---

