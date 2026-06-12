---
title: "Connection with a Win box"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by gos1 on 2008-06-18
Hi ; 
 .
  Is it possible to connect a Ubuntu 8.04 with a Win XP professional . Can windows see the Linux box ...

  Structure : I have a Hub and my ADSL ETH modem is connected to that 8 port hub . Linux desktop is connected to that hub and Win Laptop is connected to that hub too .

---

### Post by superprash2003 on 2008-06-18
CONNECT as in?? connect to share files, connect to remote control? It is possible to connect, but what do you want to do with the connection? :D

---

### Post by gos1 on 2008-06-18
For now just accessing files in the Win box . But can be controlling too if possible .

---

### Post by superprash2003 on 2008-06-18
to access files in the windows box just go to places->Computer and type smb://x.x.x.x where x.x.x.x is the ip of the windows box.
to share files in ubuntu with windows pc you need to setup samba [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)
to remote control ubuntu from windows [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine.html)

---

### Post by gos1 on 2008-06-18
Thank you very much for your reply but as a beginner . Can you please tell me how to learn the IP or a computer in the same Hub . Is there a convention for that ? Or should I use a command ?

---

### Post by superprash2003 on 2008-06-18
to find out windows pc ip go to the command prompt and type ipconfig.. you should see something of the form 192.168.x.x .. that would be the ip..
   you could also try viewing windows shares by going to places->Network

---

### Post by superprash2003 on 2008-06-18
to find out windows pc ip go to the command prompt and type ipconfig.. you should see something of the form 192.168.x.x .. that would be the ip..
   you could also try viewing windows shares by going to places->Network

---

