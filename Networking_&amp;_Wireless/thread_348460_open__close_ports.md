---
title: "open / close ports?"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by randomnumber on 2007-01-28
I need to find out how to open and close ports. I have looked and can not figure it out.
I need to open a port so that I can write some simple Java program for my class that uses sockets.

I have got my program to the point of getting info from websites and trying to connect to ports on computers. I have even gotten responses from ssh server. But I can not get through the other ports that are not open.

I have already tried fire starter to open the ports but it seems not to work or I do not understand something. I can see the ports that are open with the "network tools" port scan.

I use Ubuntu but I would like to know how to do this with XP too. 

Thanks for any help.

---

### Post by randomnumber on 2007-01-28
It seems that it may be a problem with the program supplied to us for testing. Something to do with flush(). I would still like an answer if anyone knows. It could still be a problem.
Thanks all.

---

### Post by kosmic on 2007-01-28
If there is no firewall closing/Blocking ports you can open as many ports as you want.

I don't know what your program do but you can use a socket function to open a port inside you java/C program to open a comunication between a port choosen by you and a server.

Attention that in linux the first 1024 ports are reserverd.

---

