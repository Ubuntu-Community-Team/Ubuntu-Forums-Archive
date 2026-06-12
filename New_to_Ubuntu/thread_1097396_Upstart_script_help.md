---
title: "Upstart script help"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by psatyshur on 2009-03-15
I am not sure if this is the right place for this, but this seems like a pretty basic task that I can't get to work right. I am trying to use Upstart to start a program when the system starts. Further, I would like upstart to monitor this program and restart it if it dies. I stole and modified one of the other Upstart scripts, and placed it in the /etc/event.d folder

```

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /usr/bin/deluged -d -p 58846 &> /var/log/deluged.log
```

...and this sort of works, however, there are a few problems. This may be a cosmetic problem, but when I ask for the status of the task, I get the following.

```

pat@Quasar:/etc/event.d$ sudo status deluged
deluged (stop) waiting
```

However, I am sure the task is running because I can connect to it. Also, the task is a bittorrent client called deluge, and I have noticed that the files created by this client are owned by root. I suspect that this is because the above script is run as root. I would like the program to run not as root. Is there any way to specify a different user to run the command?

I am using Ubuntu 8.04 Server Edition, if that matters.

---

### Post by psatyshur on 2009-03-16
Well, I guess that's why they call it the 'Absolute Beginner' section. :D  Apparently to run a command as a different user you can use sudo, as in

```
sudo -u <username> <command>
```

Does anyone know if you use this command as root to try to run a task as not-root, do you need to enter a password? I will try this myself when I get a chance, and report back. 

Unfortunately I just did a 'dist-upgrade' with apt and it updated me to a new kernel version. This caused a bit of problems with my system, namely the drivers for the RAID card I am using. Oops. once I get that sorted, I will update the upstart script.

Also, for anyone else that is interested, I found a page that has a bit of documentation on writing upstart scripts [here]("http://screwyouenterpriseedition.blogspot.com/2008/07/upstart-050trunk-job-definitions.html").

---

### Post by psatyshur on 2009-03-18
Looks like I am having a conversation with myself. :( Anyone out there know anything about upstart?

---

