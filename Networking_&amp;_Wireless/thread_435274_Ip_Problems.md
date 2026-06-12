---
title: "Ip Problems"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by VolvoPunch on 2007-05-06
I am running xbunutu. When i was done installing the OS i opened up the networking tool and selected my lan card to be activated. Then i set it up to be my default connection. My router is running dhcp but i don't get a connection until i enter the login into the desktop. I need the system to request an ip while on the login screen because i will be using vnc and ssh to connect with the box.

---

### Post by VolvoPunch on 2007-05-09
Ok i have still not resolved this problem. I have setup my network controller eth0 to a static ip which is 192.168.0.105 subnet of 255.255.255.0 (If i can remember correctly) and then my gateway is 192.168.0.1. When i log into the computer i have no problem firing up Firefox and getting online but when the system is at the login screen id does not have an ip. It only seems to get an ip when i login.
Edit/Delete Message

---

### Post by dbott67 on 2007-05-09
Something isn't right.  The network should be active before you reach the login screen.

The typical VNC install does not allow you to connect until you login, however, you should be able to SSH in if the computer is at the login screen.  There is a hack to allow you to connect VNC to the active destkop (i.e. screen:0 ) before logging in.

Try pinging the computer from another device on the network while it's at the login screen; it should respond.

-Dave

---

