---
title: "Some help would be greatly appriciated (remote)"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by knaves on 2007-03-27
Hey guys, it would really great if some the advanced users could give me a hand. I've had other packages of linux installed, and this is the first time i'm actually using ubuntu as I've read a lot about it. I've two computers, one running windows and one running ubuntu. I have one keyboard, one mouse, and one monitor. What i'm basically trying to do is start up the ubuntu box without any periphirals and then to remotely login to the ubuntu box that is networked with this one, and work on it this way. I've read than vnc server would be good for this. But its going over my head at the moment. Any help would be greatly appriciated. Thanks in advance.

---

### Post by chili555 on 2007-03-27
I have a home server running this way. Getting into the machine remotely is actually the easy part! Have you configured the Ubuntu box so it runs without peripherals successfully? You will know if you hook up a monitor only and it boots all the way to a desktop without help from a keyboard or mouse.

You actually don't need to have X running to do what you are trying to do, but a search of this forum has not yielded a way to automatically boot to runlevel 3. 

You will need to give the Ubuntu machine a static IP address so you can find it later. You will also need to install ssh and ssh-server.

Now we are ready for the easy part. An application in Windows called PuTTY [http://www.nbcs.rutgers.edu/ssh/putty.php3](http://www.nbcs.rutgers.edu/ssh/putty.php3) will allow you to ssh, or secure shell, into the Ubuntu machine. ssh with a user name that exists on the Ubuntu machine, give a password and you are in! Surf the web with lynx, install software with apt-get, set up a home server, etc.

Questions?

---

### Post by tombott on 2007-03-27
VNC is built into Ubuntu 6.10. but you will need to download a VNC Viewer for your XP PC.
I like to use [RealVnc]("http://www.realvnc.com") but there are many alternatives out there.

If you wish to connect to your Ubuntu box from your XP box then you will need to enable VNC on your Ubuntu box.

From the terminal:

```
gconf-editor
```

This will open the Configuration Editor.

Expand desktop - gnome - remote_access

[IMG]http://www.tombott.co.uk/ubuntu/remote.png[/IMG]

In the Top right hand window put a tick in Enabled
I like to have the prompt_enabled ticked, but this is not necessary
Then set a password in the vnc_password section.

You may need to restart your machine for this to take effect but I am not 100% sure.

If you want to connect to your XP box from Ubuntu then use Terminal Server Client Applet

Internet - Terminal Server Client

Change the Protocol to VNC and enter the IP address of your XP box.

Hope that helps.

Tom.

---

### Post by joshov on 2007-07-19
So do you use putty to ssh into the machine (without the keyboard and mouse) then vnc so you can remote desktop???

---

