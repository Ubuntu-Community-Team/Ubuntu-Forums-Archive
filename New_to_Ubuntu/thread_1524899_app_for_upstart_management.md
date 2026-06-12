---
title: "app for upstart management?"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by biji on 2010-07-05
Hi,
i've upgraded to 10.04.. great distro! i see now 10.04 is using upstart as service manager. my question, is there any application for upstart management? (for example, i dont want mysql started at boot)

thanks

---

### Post by -humanaut- on 2010-07-06
Just goto system --> admin --> settings and click startup programs (its something similar to that name AND it might be under preference's sorry I run KDE)

---

### Post by biji on 2010-07-06
can't find it there? only found Startup Disk Creator

---

### Post by sisco311 on 2010-07-06
> **biji said:**
> Hi,
i've upgraded to 10.04.. great distro! i see now 10.04 is using upstart as service manager. my question, is there any application for upstart management? (for example, i dont want mysql started at boot)

thanks

You have to edit the upstart job(s) (/etc/init/*.conf) manually.
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

> **biji said:**
> 
for example, i dont want mysql started at boot


/etc/init/mysql.conf: 
```
# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on ([b]mysql
          and [/b]net-device-up
          and local-filesystems
          and runlevel[2345])
stop on runlevel [016]

respawn

env HOME=/etc/mysql
umask 007

pre-start script
...
```

To start mysql, run:
```
sudo initctl emit mysql
```
or
```
sudo initctl start mtsql
```

---

### Post by anglican on 2010-07-06
> **biji said:**
> Hi,
i've upgraded to 10.04.. great distro! i see now 10.04 is using upstart as service manager. my question, is there any application for upstart management? (for example, i dont want mysql started at boot)

thanks

Does Boot Up Manager do what you want? It's in the repos as an acronym (I'll leave you to work it out).

H

---

### Post by sisco311 on 2010-07-06
> **anglican said:**
> Does Boot Up Manager do what you want? It's in the repos as an acronym (I'll leave you to work it out).

H

BUM doesn't work with Upstart jobs. You can only use it to manage System-V style init scripts.

---

### Post by snapy on 2010-07-06
woah.. is it true, that in Ubuntu 10.x you don't have a StartUp-Manager, for your applications?

---

### Post by sisco311 on 2010-07-06
> **snapy said:**
> woah.. is it true, that in Ubuntu 10.x you don't have a StartUp-Manager, for your applications?

StartUp-Manager is a GUI tool to manage settings for Grub (Grub Legacy), Grub 2, Usplash and Splashy. It works with GRUB 2, however some of the options available with Grub Legacy have not yet been incorporated to work with Grub 2. 

update-rc.d, sysv-rc-conf and bum are tools for managing System-V style init scripts. They are available in 10.04 but they are not able to manage the Upstart jobs.

---

### Post by snapy on 2010-07-06
> **sisco311 said:**
> StartUp-Manager is a GUI tool to manage settings for Grub (Grub Legacy), Grub 2, Usplash and Splashy. It works with GRUB 2, however some of the options available with Grub Legacy have not yet been incorporated to work with Grub 2. 

update-rc.d, sysv-rc-conf and bum are tools for managing System-V style init scripts. They are available in 10.04 but they are not able to manage the Upstart jobs.

arr.. *bite*.. that are things, like for example the file manager, that should work properly in every operating system. sry, but.. what is so complicated about managing a list of software, that should be started  in a specific order? :-&

---

### Post by yurx cherio on 2010-07-10
As linux is trying to become a more user friendly desktop system (especially Ubuntu) it must have GUI for upstart. Whether it is textual (like sysv-rc-conf) or graphical (like BUM) it doesn't matter much. Without basic tools like this Linux with desktop is still linux for geeks.

I vote for GUI. If I had time I would write one.

---

### Post by ciampix on 2010-12-29
> **yurx cherio said:**
> As linux is trying to become a more user friendly desktop system (especially Ubuntu) it must have GUI for upstart. Whether it is textual (like sysv-rc-conf) or graphical (like BUM) it doesn't matter much. Without basic tools like this Linux with desktop is still linux for geeks.

I vote for GUI. If I had time I would write one.

I agree...so vote here!

[http://brainstorm.ubuntu.com/idea/22204/](http://brainstorm.ubuntu.com/idea/22204/)

---

### Post by sisco311 on 2010-12-29
> **ciampix said:**
> I agree...so vote here!

[http://brainstorm.ubuntu.com/idea/22204/](http://brainstorm.ubuntu.com/idea/22204/)


No need for voting. 

jobs-admin is in the repositories.


[http://ubuntuforums.org/showthread.php?t=1550239](http://ubuntuforums.org/showthread.php?t=1550239)

---

### Post by aivan on 2012-03-18
Hi guys,

Is jobs-admin working for you on Ubuntu 11.10? 

It does not work on my system (I even traced down part of Python code which fails because upstart reports version 1.3 instead of 0.6 as expected).

Anyway, since other alternative is "ServiceManager" from 2009 (with quite limited features, just start/stop) I decided to try an practice some C++/Linux/GTK+ development on a new manager for upstart jobs.

Is anyone willing to test and see if the "stuff" I made so far actually does anything on your systems (currently it should list jobs and provide details about them - and running instances). 

Please tell me if you are willing to try so I can send you the binary (or complete source if you want) by email (or maybe I should place it somewhere for download?).

Regards,
Ivan (ivan.arandjelovic@gmail.com)

---

### Post by 7bit on 2012-08-04
> **sisco311 said:**
> No need for voting. 
jobs-admin is in the repositories.


jobs-admin is not of any use because there never existed any version where it actaully worked and it is still broken (12.04).

Are there any alternatives?

---

