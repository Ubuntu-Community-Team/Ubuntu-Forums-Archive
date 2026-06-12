---
title: "Xubuntu Server 8.04 Login and GUI"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by hbost on 2009-08-03
I have an old Dell Optiplex that I have set up as an Xubuntu Server (8.04) running on two Seagate 1TB drives in Raid 1.  I run Samba, OpenSSH, etc. and so far it is running well.

Being a noob, I set up the system using the GUI (xfce?) as I wanted to be able to use the Samba web-based setup program.  As I learn more, I am hoping to set up an Apache server as well.

Here is my request -- In order to save system resources, I would like to boot up the system and automatically login without the GUI to run a headless server.  However, I would also like to be able to keep the GUI/xfce option to run when I am maintaining/building/playing around with the system.

I have a feeling this is easy, but all of the options in the forum seem to point to either: a) completely removing the GUI, or b)saying that I am SOL because Xubuntu Server inherently is GUI based.  

Shouldn't there be an easy script to run on boot that gives the option to run with or without GUI? Clearly the easiest way to do it would be to default to running without GUI then run 'startx' at terminal to get graphics if I don't want to tinker with CLI.  

Also, if running without the graphical login screen, how can I automatically login at reboot/restart?  

Thanks and be kind to the noob if this is a silly question....

H

---

### Post by wojox on 2009-08-03
hmmmm... don't know xubuntu but you should be able to find your service settings and turn off Graphical login manager. On Ubuntu it's System > Administration > Services don't know xoffice. Then when you login try:
```
sudo /etc/init.d/gdm start
```
Logout
```
sudo /etc/init.d/gdm stop
```

---

### Post by hbost on 2009-08-16
Sorry for long delay in responding.  Thanks, this works.

---

