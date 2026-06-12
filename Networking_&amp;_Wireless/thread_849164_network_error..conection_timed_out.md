---
title: "network error..conection timed out"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by ub007 on 2008-07-04
I got a single PC(ubuntu server) connected to my uni network and can access the internet via uni lan.I installed ssh,n i was able to access the ubuntu host from windows vista running on my laptop(connected to uni wireless neytwork).(using PuTTy s/w here)

However when i ask my friend residing in a different country to attempt ssh connection using puTTy,the terminal opens up n then gives an error msg -network error..conection timed out

I am able to ping his machine from my ubuntu host though...

What could be wrong here?Is uni n/w firewall blocking the conn?

Thanks in advance

Cheers
David

---

### Post by superprash2003 on 2008-07-04
firewall is a possibility , also you would need to port forward 22 as SSH uses that..

---

### Post by ub007 on 2008-07-04
Thanks,how do i do a port forward>?

---

### Post by superprash2003 on 2008-07-04
well for this you need to have access to the router.. steps vary from router to router, try finding your router here [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm) .. basic steps are loggin into your router. going to the virtual server page and opening port 22.. as ip address, enter your pc's local ip address

---

### Post by ub007 on 2008-07-04
Many thanks,
I posted a similar thread elsewhere cz i needed the solution real fast before i logged off for the weekend,my apologies for that....
One of the guys mentioned that i could do a port scan on the uni n/w and run my  ssh on any of the open ports...though its not appropriate to do that,i would like to test out how that works.....i can find out open ports easily using nmap,but do not know the latter part which is running ssh on an open port of the uni n/w...

---

### Post by superprash2003 on 2008-07-05
the suggestion given by the other person may not work..cause even if ur uni has open ports, it may not be forwarded to your computer.. anyways to change the port from 22 to something else edit your /etc/ssh/sshd_config file.. go to the terminal and type sudo gedit /etc/ssh/sshd_config .. and change 22 to whatever port is open

---

