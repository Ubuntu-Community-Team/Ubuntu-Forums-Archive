---
title: "Remote Connect Computers"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by XitNow on 2011-02-10
This is going to be a total noob question and I am sorry in advance.  I have two computers, when they are both connected to my home network I have no issue remote connecting the two.  One is my mother in laws and when I bring it over to her house I can't make the two computers talk to each other over the Internet.  

I use ifconfig to find the IP address, but when the two computers leave the same network this doesn't seem to work.

Anyone have suggestions.....?

---

### Post by Grenage on 2011-02-10
> **XitNow said:**
> This is going to be a total noob question and I am sorry in advance.  I have two computers, when they are both connected to my home network I have no issue remote connecting the two.  One is my mother in laws and when I bring it over to her house I can't make the two computers talk to each other over the Internet.  

I use ifconfig to find the IP address, but when the two computers leave the same network this doesn't seem to work.

Anyone have suggestions.....?

I'm sorry, but could you please elaborate or rephrase the question?

Can you connect over the internet?
Can you connect locally?
Are the computer IPs static, or Dynamic (from a router, et cetera)?
How are you connecting (SSH/VNC/SMB)?

---

### Post by XitNow on 2011-02-10
Mother in law - laptop - Ubuntu
Mine - Desktop - Dual boot 7/Ubuntu

Setting remote desktop connection on laptop to accept incoming, using VNC viewer from 7 to take control

Connection when computers are local on my network works great.

Connecting via internet is where problems occur. 

Connections must be Dynamic, both are attached to router.

---

### Post by Grenage on 2011-02-10
Thank you.

Normally the Remote Desktop uses UPnP to automatically forward ports on the router.  When you are remotely connecting to your Mother in-law's computer, I presume that you are connecting to whatever her external IP address is, which I also presume is dynamic.

If the router doesn't automatically forward the ports, you'll want to change the router's setting so that her computer always gets the same IP address; it should be referred to as a DHCP reservation, or similar.

You would then configure a rule (again, on the router) to forward port 5900 to that reserved IP, which will be her computer.

If her router supports a dynamic IP service, such as dyndns.org, you can make life easier by also setting that up.

---

### Post by Cheesehead on 2011-02-10
The details of connecting two computers across the internet using VNC are at [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

I use reverse-VNC connections myself, and heartily recommend that method. It keeps all the weird configuration at only your end. The other end simply needs to know "Phone me, then click on this". At your end, there's quite a bit to do (and undo once complete), including:
1) Set up port forwarding on your router.
2) Open the ports on your system.
3) Start the VNC server in reverse-connection mode.
4) Tell the person at the other end your IP so they can initiate the reverse-connection.

---

