---
title: "How to check/enable/disable the services"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by john77eipe on 2010-10-16
How do I view/enable/disable the services that are started when the system boots?

I have installed tomcat and PostgreSQL and these services starts by default. I would like to disable this feature. And manually start a service when needed.

---

### Post by TeoBigusGeekus on 2010-10-16
Administration>System(or Preferences, can't remember)>Startup services.

---

### Post by john77eipe on 2010-10-18
I don't find "services" option in Ubuntu 10.04.1.

---

### Post by amjjawad on 2010-10-18
> **john77eipe said:**
> How do I view/enable/disable the services that are started when the system boots?

I have installed tomcat and PostgreSQL and these services starts by default. I would like to disable this feature. And manually start a service when needed.

System > Preferences > Startup Applications

---

### Post by chideock on 2010-10-18
System-Administration-System Monitor 
pick the tab you want

---

### Post by john77eipe on 2010-10-18
After doing some search found that there are 2 applications for easing service management.
rcconf and bum.

Which should I prefer? 
There got to be a preinstaled application like Services in Ubuntu 10.04.

---

### Post by Morbius1 on 2010-10-18
The problem is "upstart". Some services are controlled the old way and you  can manage it with rcconf and BUM and some services are controlled by upstart.

You need to control upstart services manually. Sisco311 explains this far better than I could: [http://ubuntuforums.org/showthread.php?t=1524899](http://ubuntuforums.org/showthread.php?t=1524899)

I don't think there is a GUI for upstart yet.

---

### Post by john77eipe on 2010-10-18
I installed BUM. It displayed both tomcat and postgre. So got it disabled. Thanks all.

---

### Post by john77eipe on 2010-10-18
Morbius1@ question for you.
Please explain what startup jobs mean. 

I don't see tomcat or postgre in System Monitor. So it didn't start right?

---

### Post by john77eipe on 2010-10-20
I read that /sbin/init process uses an entry in /etc/inittab for system’s default run level to run scripts that start various services at boot time.

But I don't find inittab under my etc folder!

---

### Post by soldier1st on 2010-10-22
may i ask why do you want to touch the default services? tweaking them won't improve performance but if one is causing a problem then changing them can help.

---

### Post by bhy on 2011-03-01
Well, since I only have 512 MB of RAM on this machine, and I know I don't need stuff like Avahi, is it really so weird that I want to disable it? That fact that the only way to do this is by editing config files is certainly a serious error (not that it's difficult, but it takes a lot of time). All major distros have had tools for this since years ago.

---

