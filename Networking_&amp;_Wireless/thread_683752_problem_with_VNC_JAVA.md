---
title: "problem with VNC JAVA"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by victor-be on 2008-01-31
Hello 

I experience problem with connecting myself to vnc via http-java connection (I don’t have problems . I want to connect on my (Ubuntu) with my Windows XP. I’ve configured my router and redirected ports 5800 to 5800 and 5801 to 5801. 
I’ve installed tightvncserver on my Ubuntu…
The first strange think is that, when I type the IP [http://xx.xxx.xxx.xxx:5801](http://xx.xxx.xxx.xxx:5801), windows can reach Ubuntu computer (the name of the linux distant pc appears on my windows desktop), but after entering the password, it says there is an error and that it cannot connect to port 5901… 
I opened the port 5901 on my Ubuntu firewall (firestarter); now the connection can be done! (without changing the port redirection) but I cannot see the desktop of my computer, but only a terminal to run application in command line; however, if I run, for example, a multimedia player (Totem), I can see the graphical interface…

I’ve searched around the web over and over… no answer this time. And I’m a very beginner… but more and more passionate about it.
Could someone help me?

I don’t event know on which PC is the problem.
I guess the problem is with java, but how diagnose it?

Thanks a lot

---

### Post by Yhetti on 2008-01-31
How did you start the VNCServer?

By default, most Linux VNC servers run in a new X session, *not* the X session that you would normally use for your desktop.  That's because the original assumption for VNC in Linux is that you would be using it to provide lots of desktops for lots of people, not remotely seeing your own (single) desktop.

Are you using the server built in to Gnome or KDE, or something else?

---

### Post by victor-be on 2008-01-31
i start the server by typing $tightvncserver (which i've installed) in a terminal; if i don't do that it won't connect; after that, i can only connect (from my web browser) when i type xx.xxx... (internet IP):5801 (and it it redirected somehow to the port 5901, that i have to open... i don't understand why this java connection has to use that port...)

 i'm working with a gnome environment

---

