---
title: "PuTTY : Not exporting DISPLAY"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by gnikol on 2007-11-07
Hi , 
I want to connect remotely from a pc running windows 2000 to a pc running ubuntu 
ssh server is running on ubuntu , and I'm connecting normally using XWinLogon. 
I tried to use PuTTY  instead with no success . 
From Windows I'mn running PuTTY (ssh connection to port 22)
I'm connecting normally to the ubuntu, but it brings me to a command line window
On this window i try to run firefox for example (exporting DISPLAY first): 

$ export DISPLAY=169.254.127.99:0.0   (it is the ip adress of the windows pc)
$ firefox &

but I get the message: 

(firefox-bin:5448) : Gtk-WARNING ** cannot open display:

Am I doing something wrong?

---

### Post by CyberBob on 2007-11-07
Hello,

PuTTY is for connecting to a remote server with a terminal session (TTY = teletype).  If you want a graphical remote session you'll have to set up vncserver on your server running ubuntu- here is a link that explains how to do that:

[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

Once you have the server running on ubuntu, then you need to install a vnc client on the windows 2000 computer.  I've used both TightVNC and UltraVNC - both are good.  Just do a google search for those and install your preference on the win2000 machine.  Instructions on how to use the client will teach you how to make a successful connection.

Good Luck!

---

