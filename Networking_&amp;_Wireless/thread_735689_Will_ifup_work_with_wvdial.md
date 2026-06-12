---
title: "Will ifup work with wvdial?"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by joegeek on 2008-03-25
I'm using Ubuntu Feisty Server (No GUI!), named lilblackbox.  I connect to the internet via dial-up.  wvdial works great.  lilblackbox is my gateway/firewall for my network.  80% of the boxes connected to my network are M$ Windows boxes.  

I'm attempting to write a proggy (in Visual Basic (open source of course)) that'll set in the system tray as a lil red dot, you'll click on it to connect to the internet, the lil red dot turns yellow, connect to the host (in my case lilblackbox) via ssh, send the command ifup [interface (in my case ppp0)], upon connection the lil dot turns green, and monitors the connection.  If the connection is dropped it'll turn the dot red.  If the user wishes to disconnect, they click the green dot and the process is reversed.

The reasoning behind wanting to use ifup/ifdown and tools of the like is that dispite the linux flavor this is almost universal, and I imagine some people who might want to use this tool my not be using it for a dial-up connection.

**My question is:** How do I get wvdial to work with the ifup/ifdown tools (or vis versa)?

---

