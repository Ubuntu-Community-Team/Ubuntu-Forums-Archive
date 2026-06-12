---
title: "Can't access server outside LAN"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by josh_2.0@comcast.net on 2011-01-10
Hi,
I've recently set up my first Ubuntu server. I got an http server (Nginx) running and responding to requests (or, at least I thought I did). I visited the server's IP address ([http://192.168.2.4](http://192.168.2.4)) from another computer in my home, and it displayed just fine.
 
But then I visited it from a computer at my school and I got a connection error. So, I called home and had someone check the address from a computer there and it loaded fine.
 
I'm clad there is an absolute begginner's thread because I'm almost embarrased to ask this question, but what am I doing wrong?
 
Any help would be greatly appreciated.

---

### Post by DanYoSon on 2011-01-10
the ip address that you have there is the internal ip given out by your router to the computers on the network via DHCP or by you setting a static ip for the computer.

In order to access the server from outside the network you need to set up port forwarding, this is done from your routers admin interface. 

for example for http you want to forward port 80 (default) to the internal ip of your server in your case 192.168.2.4.

in order for this to work consistently you need to give the server a static ip if you have not done so yet.

hope this helps, post back and let us know how it goes

DanYoSon

---

