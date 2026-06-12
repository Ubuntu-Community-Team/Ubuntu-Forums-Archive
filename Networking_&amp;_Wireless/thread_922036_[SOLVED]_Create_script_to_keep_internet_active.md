---
title: "[SOLVED] Create script to keep internet active"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by zerox20 on 2008-09-16
Hi folks,

I would like to create a script that will ultimately run a simple command to keep my internet active at all times.  Here is what I want it to do:

Ping a random website, for example [www.google.com](www.google.com), once a minute to ensure connection to outside server is active.  If timeout occurs, run the following two lines concurrently: 
```
iwconfig eth1 essid linksys key open
dhclient eth1
```

Basically, I want my internet connection always to remain online.  I have actually uninstalled network manager because it was interfering with my wireless card.  Everytime I boot my machine, I have to run those two lines (which I am fine with).  At random points, the connection will die and I have to run those two lines again to get my connection back up and running.  I can't seem to pin down a cause for the blackout, but it happens often enough that I am searching for a solution to combat this problem.

Any tips you can offer is much appreciated.

Thanks so much!
-Matt

---

### Post by Jacobian on 2008-09-16
Well, here is a tiny script to get you started:

```
#!/bin/bash

while [ 1 ]; do
        ping -c1 www.google.com
        sleep 1m;
done;
```

Copy and paste this code into a file named "active," move it to your bin directory, and make it executable.

Perhaps the simplest way to do this would be to the Terminal and type:
```

cd ~/bin
ls
nano active

```

Now paste in the shell script code above, and save the file with a Ctrl+X.

Finally, make the script executable:
```
chmod a+x active
```

Now you can run the script from anywhere by opening a terminal and typing:
```
active
```

You could set a script like that to run on start up.

One way to do this might be to open:
System -> Preferences -> Sessions

And add your script.

Then you can improve the script so that it can restart your network connection if it ever disconnects. You can start a process in the background by appending '&' after the command.

For example, this will run your command in the background:
```
active &
```

You could use this to run two commands concurrently in your script.

Anyway, I hope this gives you a place to start. :)

I'm new to bash scripting myself!

---

### Post by zerox20 on 2008-09-30
I actually figured this out with some help from some guys on a linux listserv.  This is what I ended up doing:

I made a script called "keep_alive" that I have in my /usr/bin folder.  This script is executable and contains the following information:
```
if [ "`fping www.google.com`" != "www.google.com is alive" ]
then
        iwconfig eth1 essid linksys key open
        dhclient eth1
fi
```I then set up a cron job in root to have this program run every 5 minutes.  If it can't find google, it will attempt to reestablish internet.  This was done by typing "sudo crontab -e"
```
# m h  dom mon dow   command
*/5 * * * * /usr/bin/keep_alive
```I also threw the "guts" of the script in /etc/rc.local so that when my computer logged on, it would establish internet.

---

