---
title: "sshd need help!!!"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by joereith on 2007-05-22
how do i do what this guy is asking for?


Quote:
Originally Posted by joereith
 ip:192.**.*.*
I think that is the internal IP address of your router. Does your machine connect to a router? If it is, then you need to go into your router and open port 22 for incoming traffic. Then, you need to redirect that incoming traffic to your Ubuntu machine--192.168.1.65. Then, I need to know the actual IP address of your machine (you can find that out while you are in the router) so I can connect to it.
__________________

---

### Post by kilroy423 on 2007-05-23
He is asking if your computer is directly connected to a modem or if it has a router inbetween.  Then he wants you to go to the routers config(if you use one) which is located at the routers ip address and open port 22.  After completing that he wants you to tell the router to take all traffic on port 22 and forward it to your machine running ssh.  Once this is accomplished a machine from outside your LAN will be redirected to your ssh machine.  

Please in the future do not post with just ???? and utilize the tools that you have before your fingers by STW, STF, and RTFMing. ;)

dan

---

