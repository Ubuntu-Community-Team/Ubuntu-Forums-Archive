---
title: "Kind of new at this. Router and networking scheme"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by iand675@gmail.com on 2006-09-14
Hi, I have a linksys router running dd-wrt on it and a dyn-dns account that I'm trying to set up. I basically have no network configuration knowledge aside from some basic networking concepts and have no idea what kind of programs are out there. My concept of what i'm trying to do is this:
1. be able to use any internet browser to access a home ftp server.
2. browse websites with my home internet connection using another computer's browser. (ssh is not an option)
3. have windows and ubuntu to be able to run the same configuration.
4. maybe stream my music from my computer.
You see, I am currently needing to access my computer at a location that has a windows network that blocks all inbound and outbound connections except for internet explorer. Plus the site filter it has set up is way too touchy (i.e. it blocks me from googling wine or wine-doors because it thinks i want an alcohol related website.) If anyone can help me figure this out I would be extremely grateful!
Thanks

edit: ubuntu center looks good, but I would still need an online proxy thing that used my home internet connection

---

### Post by tbonius on 2006-09-14
From the sounds of it.. they probably dont even allow inbound connections.  So you want to be able to access your computer at home (through your router) and open a "remote desktop" so that you can browse websites remotely?

Install tightvnc on your Computer at home.. configure it to listen on port 80.  Open and forward port 80 on your router to your internal Ubuntu computer.  Install tighvncclient on your desktop at work and access your computer at home.  Surf away.

Or

Install tightvnc on your Computer at home.. configure it to listen on its default port (5800).  Open port 80 on your router and forward it to your default VNC port on your Ubuntu computer (5800).  Install tighvncclient on your desktop at work and access your computer at home.  Surf away.

Or 

Configure SSH on your Ubuntu computer to listen on port 80.  Enable X forwarding.  Open port 80 and forward it on your router to your internal Ubuntu computer.  Install an X-client at work and connect via SSH on port 80 to home computer and run an Xsession.  Surf Away.

Or

Rejoice in the the idea of ingenuity out of necessity and describe more about what you are needing.

Or

Give up and cry.  Bang your head against our keyboard.  Long for better days when most IT personnel had no idea what they were doing.  Go to work for Microsoft.

---

### Post by iand675@gmail.com on 2006-09-14
well thanks for the response. that reminds me of something. The system blocks installation of new programs. Basically novell client kills any unauthorized processes or programs, which is why I need to be able to access my home computer with only a browser. Any sort of java program or servlet or something that could basically do vnc within an unmodified browser and an http or https connection?

---

### Post by cbaoth_2000 on 2006-09-14
Remote Desktop through internet explorer

do what the man says about the tight vnc on the home comp and then from work use internet explorer to access your home comp either by its IP address(if you have a paid for static IP) or by the Dynamic DNS application which keeps pinging your home comp and logging its present dynamically isp assigned ip address to a DNS name such as "homeubuntu.mine.no-ip.com" meaning that from internet explorer just typing in [http://homeubuntu.mine.no-ip.com:5800](http://homeubuntu.mine.no-ip.com:5800) would give you your home computer via remote desktop served via java or if only being able to get out on port 80 typing [http://homeubuntu.mine.no-ip.com](http://homeubuntu.mine.no-ip.com) and pre-setting port forwarding on your lynksys router to the tightvnc or realvnc designated port ...vnc from [www.realvnc.com](www.realvnc.com) is free and for linux and all are configurable to any desired port setings you require

---

### Post by iand675@gmail.com on 2006-09-14
Sounds good :)
can I upload and download files with vnc?
And also, does sound work? Or will I need something seperate for that?

---

