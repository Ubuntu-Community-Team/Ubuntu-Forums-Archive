---
title: "lost internet in local network"
date: 2016-09-13
forum: Networking &amp; Wireless
---

### Post by goeh on 2016-09-13
Hello all,

I have trouble with internet in home local network.

Have a router, wifi clients (iphones, macbook and windows laptop) and cable clients (tv, mediaplayer, ubuntu server)
i use ubuntu server for DLNA and torrents.
Some time after turn on ubuntu server internet in local network is going out.
Means iphone or windows laptop cant go to the internet. Ubuntu server cant as well
Have no ping to google.com for example but local network is still working. TV is playing movies from ubuntu server via DLNA.
If i turn off ubuntu server internet is immediately coming back.

Thanks in advance

PS.Sorry for my English.

---

### Post by TheFu on 2016-09-13
Cannot tell from the description, but please try to ping 8.8.8.8 from each device and report back on how that works for each device. That includes doing it from the router - most home routers have a command interface page where you can enter the command to be run.

Often, the issue is just DNS, not actual internet connectivity. Sometimes ISPs make a mistake and don't set the DNS correctly, so you can override that at the router to an alternative DNS provider.

But first, run the pings from each device requested.

At this point, I can only guess that maybe the Linux machine is getting the IP address of the router's LAN interface, somehow. Don't know how that can happen, but checking all the IPs for each machine will confirm if this is or isn't the issue.

---

### Post by DuckHook on 2016-09-15
*Thread moved to **Networking & Wireless** as the more appropriate forum.*

---

### Post by SeijiSensei on 2016-09-15
Turn off torrents and see if the problem goes away.  Some cheaper routers do not have enough memory space to manage the number of simultaneous connections that torrent clients generate.  Eventually the router "falls over," and access to remote network sites goes away.  If you must run torrents, then set up your client to do so overnight.

---

### Post by TheFu on 2016-09-15
Good idea about the torrents!

---

### Post by SeijiSensei on 2016-09-15
Been there, done that!

---

