---
title: "+ Add to Panel not working"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Sjeti on 2008-12-17
So when I first started learning linux I was a little careless with my chmod and chown command, I believe I got a little overzealous and might have screwed some things up.

I'm thinking that is the cause, but when I go to "Add to panel" and then add various things like window selector and most of the important panel options, they simply don't appear.

Some things do appear...but I can't rightclick on them to change the settings.  Any clue what is going on or how I might fix it?

---

### Post by Michael.Godawski on 2008-12-17
Without knowing the your chmod and chown adventures it is difficult to tell what is wrong with your system. Do you remember some stuff?
 
Tip:
All your commmands started with sudo, executed with root privileges are stored in this log:
     ```
/var/log/auth.log
```     You can either access it by System - Administration - System Log - auth.log, or by typing into the terminal ```
gedit /var/log/auth.log.
```     This log is very useful if you messed something up, and want to look up the commands executed with sudo.


There is also a log which stores every command you type into the terminal. It is located here:
     ```
~/.bash_history
```

taken from [http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)

---

