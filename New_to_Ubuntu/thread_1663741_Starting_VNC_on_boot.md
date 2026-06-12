---
title: "Starting VNC on boot"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by klndz05 on 2011-01-10
I'm attempting to start VNC on boot in order to work on a display-less machine I have running 10.10. I've looked into using x11vnc, vnc4server, and vncserver, however I can't quite figure out how to make it work. I figured using a symbolic link and init.d would be a good solution, and found this mentioned in a previous thread ([http://ubuntuforums.org/showthread.php?t=189555](http://ubuntuforums.org/showthread.php?t=189555)), however; it didn't seem to work. I've read around other solutions, but they haven't yielded anything for me either. Is it because there isn't a desktop to view, so I cannot connect to it? Is there even a way to just log in to the desktop via SSH? This is really a very rare instance where I'd like to use VNC, so even a temporary solution is alright. I plan to VNC in from a Mac running OS X 10.6.6.

Thanks!

---

### Post by TechWiz2100 on 2011-01-10
VNC needs something to display, otherwise its useless and displaying nothing but black lol

If you want displayless you need SSH but if you want to show a desktop then it has to be running for VNC to be able to send it. There are other options but I doubt those other options will function nearly as easily as VNC so you're better off letting Ubuntu load in Gnome or whatever and putting a shell script into init.d or on cron that launches your daemon.

---

### Post by Cheesehead on 2011-01-10
TechWiz2100 is 100% right about needing ssh. Do that first, and VNC will follow quite easily.

SSH gives you a way to start/stop your X server and VNC remotely, which can save your headless machine a lot of overhead. SSH provides tools that VNC later needs (like IP addresses). SSH also provides a secure connection for the later VNC session.

So I recommend SSH is the service you want to start at boot instead of VNC.


One way to set it up:

1) Start SSH on remote machine on boot.

2) A VNC-start script on your machine:
- opens any necessary ports on your router and/or firewall,
- starts your VNC server,
- uses SSH to log into the remote machine, 
- start the remote X-server, 
- start a reverse-VNC connection from the remote machine (This keeps config of the remote machine much simpler - most problems will be at your end instead of the remote end)

3) A VNC-stop script on your machine:
- stops your VNC server,
- uses SSH to log into the remote machine, 
- stops the reverse-VNC connection from the remote machine,
- stops the remote X-server, 
- closes the ports on your router and/or firewall

---

### Post by pricetech on 2011-01-10
Definitely SSH for your connection, but I recommend NX from nomachine dot com for your GUI.  Just plain works.

---

### Post by perspectoff on 2011-01-10
SSH and VNC instructions:

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Remote_Access)

or

Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#Remote_Access](http://kubuntuguide.org/Maverick#Remote_Access)

Includes method for autostarting X11VNC at boot time via script.

---

### Post by klndz05 on 2011-01-10
Thanks guys, I'll get on that and see how I do. I'm already SSHing into the computer and really have set up nearly everything how I want it, but I just like to have everything working, and this is one of the things that was bugging me.

---

