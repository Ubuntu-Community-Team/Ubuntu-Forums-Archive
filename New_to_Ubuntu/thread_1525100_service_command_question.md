---
title: "service command question"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Corrupter on 2010-07-06
i am currently adding a service based application to my ubuntu server and i have the /etc/init.d/script in place with the proper permissions as well as the script configured properly as well as the application and its required bits in the correct places. ie; /opt/appname

i can call the script through /etc/init.d/script start|stop|restart|status etc just fine.  It loads everything perfectly fine and works as intended with zero flaws.

However since the introduction of the service scriptname start|stop|restart|status implementation when i attempt to use this command to shorten what i have to type the script returns that it cant find a required file. (in this case a log file which is there and the permissions are checked accordingly).  The script in the /init.d/ folder requires the app to be run under a certain username and that is set accordingly with the appropriate permissions.  What im wondering is the following:
is service appname start trying to run the app in a path that isnt where the files are actually located and do i need to revise my script to handle this path or what.  furthermore im logged in as root while testing all this but when the service appname start is called its trying to run the program using a different username, is this somehow causing a conflict or confusion.  Thanks a ton for your input.  i look forward to your help.

---

### Post by Corrupter on 2010-07-06
so a little more info:

it seems to be related to a path access problem, the startup script is executing the program from its directory but for some reason the program doesnt see the files thats in the directory with it even though its executing from the same directory.

I dont know if this has anything to do with permissions and path or just path or just permissions but i've been over it a few times and tweaked some stuff and havnt gotten any further then figuring out whats happening.

The only other thing i can think of is i have a jailkit installed which is [http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/) but this application is a completely different non-webpage related app that runs on its own user which i had to create.  The user i made has a standard /bin/sh and its home directory is actually the /opt/appname folder so its home directory by default is where the program physically is.

Any thoughts?

---

