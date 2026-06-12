---
title: "[SOLVED] Problems VNCviewer --&amp;gt;Ultravnc Sc"
date: 2008-08-14
forum: Networking &amp; Wireless
---

### Post by jackuss on 2008-08-14
Hello,

I'm trying to create a (Reverse) VNC connection from my parents Windows 98 computer to my Ubuntu pc, via the program UltraVNC_SC. I got a couple of problems here:
First of all, when I enter "vncviewer -listen" or "vncviewer -listen 0" in a terminal, I get the message: vncviewer: ListenAtTcpPort: bind: Address already in use". I get this message even if it is the first time I type it. Is there a way to stop this? To kill vncviewer more or less. I don't see it when I enter "top", to see all the active processes. 

Second... Is there a way to start using vncviewer. When my partents doubleclick on the icon to start Ultravnc_sc, I don't get a connection. I tried the Remote Desktop functionality in Ubuntu, and I installed UltraVNC on Wine. None of the two works. Even if I enter the WAN IP address in the "Connect box"there is no connection. On my firewall the port 5500 is forwarded.

I have no idea what else I can do now... Hope anybody can help me.

Thanks in advance

I found the solution... I opened up another port, this solved it.
But isn't it strange that port 5500 is always listened to, even if you just started your computer

---

