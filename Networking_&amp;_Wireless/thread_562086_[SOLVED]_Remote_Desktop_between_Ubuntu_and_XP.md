---
title: "[SOLVED] Remote Desktop between Ubuntu and XP"
date: 2007-09-28
forum: Networking &amp; Wireless
---

### Post by LauraSakura on 2007-09-28
Hello. I want to remotely access my windows XP computer from my Ubuntu one. However, I don't have Windows XP professional, so It does not include the Remote Desktop Server. I looked around online, but didn't find a remote desktop program that works between linux and xp and has a windows server. Any ideas? (Sorry, I'm new at this sort of thing). Thank you

---

### Post by cwhitehouse on 2007-09-28
You can use a VNC client.  Search Google for VNC clients, there are quite a few good ones out there.  Once you have it installed and you have allowed remote connections from your Linux box, you should be able to launch VNC and type in the name of your Linux box and you should be able to connect that way.

---

### Post by LauraSakura on 2007-09-28
Sorry, I may not have explained clearly. I have VNC clients on my linux pc. I want to access my windows computer from my linux one. My problem is finding a VNC server for my windows xp computer.

---

### Post by namich2007 on 2007-09-28
When you say access :

are you trying to get to files you have on your windows pc  or are you trying to connect to your windows pc to administer it remotely

---

### Post by LauraSakura on 2007-09-28
as in have the screen of that computer appear on my linux one in a window. So remote desktop. I was able to do it through Hamachi and VNC, but that doesn't seem to work when I'm on wireless, only when plugged in through ethernet. Not sure why

---

### Post by cwhitehouse on 2007-09-28
You can try one of these windows VNC servers.

[http://www.uvnc.com/](http://www.uvnc.com/)

[http://www.realvnc.com/index.html](http://www.realvnc.com/index.html)

[http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by LauraSakura on 2007-09-28
looking more into things, I think the problem isn't i need a different vnc server on my windows machine. Somehow, my linux computer is connected twice in the hamachi network with 2 different ip addresses. Earlier through hamachi I was able to use vnc to remotely view my windows desktop, but now I just get:
vncviewer: ConnectToTcpAddr: connect: No route to host
Unable to connect to VNC server

---

