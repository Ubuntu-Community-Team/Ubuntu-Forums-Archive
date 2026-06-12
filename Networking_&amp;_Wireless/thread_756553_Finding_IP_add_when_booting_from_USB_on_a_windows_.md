---
title: "Finding IP add when booting from USB on a windows box"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by madtinkerer on 2008-04-15
Hi all,

I've made a persistent live USB install of 8.04 beta to use at work.  I teach at a university and I'm always going into different classrooms with systems in various states of awful, virus ridden windows installs.  My problem is that all of the computers on campus use static IPs, so configuring my networking without first booting into windows to get the IP information is a pain.  Does anyone know if there is a file similar to /etc/hosts in an XP system that can be parsed from my linux USB environment so I can get the IP information?  I'd like to write a script that would gather that info then create an ifconfig command that I could use to setup networking in the linux install.

Thanks

---

### Post by jetsam on 2008-04-16
There's a hosts file in Windows (usually in C:\WINDOWS\SYSTEM32\DRIVERS\ETC), but I don't think it will have what you're looking for inside.  The one on my xp machine just has "127.0.0.1 localhost" after some comments.  

Curiosity made me Google, which led to this:
[http://www.codeproject.com/KB/IP/obafindingipinformation.aspx]("http://www.codeproject.com/KB/IP/obafindingipinformation.aspx")
I'm afraid what you want is stuffed inside the registry.  

I don't know Windows networking in depth, though, so maybe there's another option out there...

**Edited to add**: Could you get IT to reserve a single ip for your wandering system?  If the ip address is set locally on each machine, there shouldn't be a reason why you couldn't set a different one when you boot up.

---

