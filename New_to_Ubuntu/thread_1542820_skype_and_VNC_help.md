---
title: "skype and VNC help"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by antonio.segalini on 2010-07-31
Hi guys

I have a messy situation to handle. I am actually abroad my country where my wife is living temporarily. Until june we communicated through skype and everything was just fine. But when I came back i have updated her system (ubuntu 10.04) with the last updates and maybe change some skype audio options. 
After I came back to my working place and now skype is no longer working properly: I can call her  but her audio is awful, slowed in some sense, like if I am talking to an artificial voice. her microphone (an external one) is fine because we tried it with another PC.

I am pretty sure that i could solve this problem by seeing the desktop with VNC but I do not know how to install it and, in particular, how to connect with it because she is using a wireless router to connect with me (and therefore a DHCP address). Is it possible to connect with that PC? Or maybe even SSH could be just fine. I never connected to a PC with dynamic IP.

Besides, here I am using MAC...

---

### Post by HermanAB on 2010-07-31
Well, what is your wife using???

If she is using Windows XP Pro, then enable remote desktop and connect with rdesktop from the Mac.  Forward port 3389/TCP in the home router to the PC.  The DHCP address should always be the same - don't worry too much about it.

Otherwise, use some sort of Reverse VNC.  Put your MAC online and let her connect to it.  This may be easier to execute.
[http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)

This one is usually easiest to get to work.
[http://www.vncscan.com/vs/oneclickVNC.htm](http://www.vncscan.com/vs/oneclickVNC.htm)

---

### Post by antonio.segalini on 2010-07-31
she has ubuntu 10.04. I am also under a router, so my address is DHCP even if I think I can retrieve it

---

### Post by antonio.segalini on 2010-07-31
Let's assume I can retrieve her IP Address (I do not know how now but I can figure it out). Can I connect with SSH to install the VNC packages?

---

### Post by Irony on 2010-07-31
> **antonio.segalini said:**
> Let's assume I can retrieve her IP Address (I do not know how now but I can figure it out).
Just tell her to go to [http://www.whatismyip.com/](http://www.whatismyip.com/) before you connect and she reads it out to you.

---

### Post by antonio.segalini on 2010-07-31
Is there any easy solution like logmein for mac or windows?

---

### Post by antonio.segalini on 2010-07-31
i got the IP but the connection times out, I guess it is the router firewall. I never configured that one

---

### Post by YesWeCan on 2010-07-31
No problem.
You need to install SSH server on the Ubuntu box. 'sudo apt-get install ssh'
Then you need to know both the router public IP address and the IP address of the Ubuntu box. A hole in the routers firewall is needed. The router needs to forward public port 22 requests to the Ubuntu box IP address. This needs to be set up in the router configuration.
Then from your MAC you use SSH to connect to the router public IP address and the router forwards your connection to the Ubuntu box. You should now be connected by SSH.
To use VNC is a little more tricky because it uses different ports to SSH. On the Ubuntu machine you can either run Remote Desktop (aka Vino to see the actual local desktop) or you can run tight VNC server (to see an independent desktop instance). In either case you need access port 5900 (vino) or port 5901 (tightvnc) and possibly 5800. You can do this using SSH port forwarding from your MAC (in which case the ports are tunneled thorugh the existing port 22 connection) or you need to forward these ports along with 22 in the router config. (note: it isn't secure to use VNC ports over the public internet).

In future, I would recommend setting up OpenVPN server on the Ubuntu machine and a client on your MAC. OpenVPN is a very reliable and effortless, encrypted tunnel which connects the two computers together. I use a VPN point-to-point tunnel for remote access to a Ubuntu server and use tightvnc.

---

### Post by YesWeCan on 2010-07-31
I am not sure what is causing your Skype troubles. I am using 10.04 with Skype and it is ok although from time to time my brother sounds like Mickey Mouse and I have to hang up and phone him back. :p It may be worth uninstalling and reinstalling Skype; I am not convinced Skype for linux is as robust as other linux apps. The upgrade to 10.04 may have messed up the connections between Skype and Pulse Audio or something else.

---

