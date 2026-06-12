---
title: "Cron Questions"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by gali98 on 2009-09-10
Okay. So I am running a bitnami module of Moodle.
This works great, except when the server is rebooted. (I work for a school. In our town, we lose power quite often.)
So I just figured I could add a cron job @reboot to run the start script for the server.
So here are my questions:
First, will an @reboot tag even work for a normal user? (The way bitnami works is it runs as the user on a nonprivileged port. I.e. not root or apache, etc...)
If it does work, does the user first have to log in for cron to run?
Thanks!
Kory

---

### Post by MrWES on 2009-09-10
If you need root priveliges to run the script you can put the @reboot in root's cron:
```
sudo crontab -e
```

Bill

---

### Post by gali98 on 2009-09-10
No... That's not what I mean... I need it to run as the user.
I am just not sure if @reboot will work for a normal user with cron.
That's my question. (Thanks though :) )
Kory

---

### Post by ukripper on 2009-09-10
> **gali98 said:**
> Okay. So I am running a bitnami module of Moodle.
This works great, except when the server is rebooted. (I work for a school. In our town, we lose power quite often.)
So I just figured I could add a cron job @reboot to run the start script for the server.
So here are my questions:
First, will an @reboot tag even work for a normal user? (The way bitnami works is it runs as the user on a nonprivileged port. I.e. not root or apache, etc...)
If it does work, does the user first have to log in for cron to run?
Thanks!
Kory

why not just put your scripts in /etc/rc.local and it runs on server  everytime it reboots, saves you cronning for every user?

---

### Post by DaithiF on 2009-09-10
Hi
i would agree on rc.local as being possibly a better place for this, but to answer your question, yes @reboot will work for an individual users crontab, and no, they don't have to be logged in.

---

### Post by gali98 on 2009-09-10
Thanks guys... :)
Wouldn't putting it in rc.local run it as root? I know a little about runlevels and such, but I've never researched much into the script part of it.
I think I will still use cron, because I only need to run one command, and the script is already in the moodle directory...
Kory

---

### Post by DaithiF on 2009-09-10
> **gali98 said:**
> 
Wouldn't putting it in rc.local run it as root?
Yes, but to run as a different user you can do:
```
su - yourname -c "/path/to/command"
```

---

### Post by gali98 on 2009-09-10
I have so long wondered how to do that. I knew you could but never found it in my quick research. Thanks so much!
Kory

---

