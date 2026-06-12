---
title: "X server"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by undo123 on 2011-06-26
I have been having problems for weeks with the x server.
When I boot up and select Ubuntu from the list the program load and all I get is the command prompt.  I reboot the computer and this time select Ubuntu recovery from the list. That boot up to the list of options and I pick run in low graphic. I then get the list of options were I pick reconfigure graphics.  I go though all the part to reconfigure the xconfig file then click on the restart X server and up come the desktop and all is well, but when I reboot the computer I just get the command prompt again so, should I be saving some settings when I have got the xconfig set up or is there something I am not seeing at all or is there a way of loading the desktop from the command prompt?

James

Roses are red violets are blue and I am in a stew over this.

---

### Post by Gone fishing on 2011-06-26
I think this will work

Get the box up and running then goto tty1 (alt control F1) run ```
sudo service gdm stop
``` then ```
sudo X -configure
``` then restart X with ```
startx
```. 

In you home directory you should have a file called xorg.conf.new if this is copied into /etc/X11 as /etc/X11/xorg.conf then ubuntu will know how to setup X each time you start.

---

