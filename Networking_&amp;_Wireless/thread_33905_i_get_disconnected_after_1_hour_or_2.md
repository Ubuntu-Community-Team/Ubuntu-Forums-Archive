---
title: "i get disconnected after 1 hour or 2"
date: 2005-05-12
forum: Networking &amp; Wireless
---

### Post by El Menda on 2005-05-12
hi. my problem is the next.
i installed ubuntu hoary without any problem. i can stay in the internet and i get very good downloads and uploads, but after 1 or 2 hours i get disconnected, and i dont know why. i dont open programs or do something strange.
what can i do?
i have ethernet card integrated to the mother board, and ITS NOT WIFI OR WIRELESS

---

### Post by grakhul on 2005-05-12
I also am having this problem.  I thought it was resolved by following a couple of the tips I read in earlier sections but the problem persists.  I am pretty sure that a module in Ubunut launches at this interval and causes the internet connection to stop functioning.  What that is I havent determined as I am new to linux.  I am going through my /var/log/messages and my /var/log/syslog and have yet to find anything.  
Tell me more about your issue and we will compare to see if we can isolate this issue.

---

### Post by grakhul on 2005-05-12
So so far I have disabled IPv6 in Firefox, and aliases.  I even terminated the ipv6 ko file located in the modules dir.  I seriously doubt though, that it is the IPv6 causing this issue.  If it were the IPv6 implementation, then I would expect other issues to surface with the other protocols that remain uncommented.

Since the only type of connection I have tested has been my Wireless connection.  I want to see what happens when I remove the wireless connection and plug myself directly into the router<hardwired>.  I will surf the internet with my hardwired connection for about an hour or so, to see if the issue resurfaces.

Again:  I think this is more of an issue related to some module, process or script that launches when a certain event is met.  I think that this module, process or script is causing the disconnect.  

I once had a SuSe install that caused disconnects once the fan started blowing.

---

### Post by foustware on 2005-05-12
hi, i had to set up dsl with pppoeconf and was all fine. then a couple of days later i realized i was losing the connection from time to time. i started the networking service using the bootup manager. i don't no why it wasn't set to start at boot before, but once i started it and set it to run during boot i haven't lost a connection, so i hope it's not just a fluke. i also got pon to start at boot by editing /etc/ppp/pppoe_on_boot to:

#!/bin/sh

PATH=/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin
export PATH

modprobe -q pppoe

exec pon dsl-provider 

now all is good. Ubuntu is absolutely the best linux distro i have ever used. i can't blame the developers of the distro for watching their backs with the multimedia stuff, but a better internet connection app and default network settings out of the box would be good. also to note is that for once every app on my pc was installed from synaptic. i can't believe for once there are so many repositories that every app i need or want or am curious about is just a search and download away from within synaptic. and they all work. and the unofficial guide is icing on the cake! Windows stinks and i'm going to get as many windows users i know to at least dual boot with ubuntu!

---

### Post by El Menda on 2005-05-13
well, i dont know why, but i dont loose conection now. i've only been doing some changes to my system, but nothing about the network lol
thanks, and see ya guys

---

### Post by El Menda on 2005-05-14
i've had that problem again.
the only thing i've done is:
#ifdown eth0
#ifup eth0
and i've had entablished connection again. is there any way to do this automatically if the connection doesnt work?

---

