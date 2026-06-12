---
title: "Remote desktop help"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by lint98 on 2008-11-06
Hello,

  I was wondering if anyone could tell me how to use remote dektop.

I have a two computers.  One at work, and one at home.  At home im running Ubuntu 8.10 and at work Windows XP SP3.  I want to connect to my home computer from work, and perhaps vice versa if its not too much trouble.  I've never used any kind of remote desktop or VPN before so a link to a good how-to for exactly this kind of setup or a thorough explanation would be appreciated.  

ive set up tightvnc on my home computer now. Is it as easy as downloading tightvnc on my work computer and connecting to my public ip at home to access the home computer?

Thanks

---

### Post by and.duncan on 2008-11-07
For your home computer you will need tightvncserver, is this what you have? the client/viewer is not necessary.

You also need to make sure the port your vnc server is running on is routed to your home computer.

Then it should be as easy as connecting from work with the client/viewer.

note: I haven't actually done *this*, I have used UltraVNC on a windows computer and connected to that with the 'Remote Desktop Viewer' that came with Ubuntu. I think the gist is the same though.

---

### Post by kerpow on 2008-11-07
You will run into problems with NAT routers and firewalls.(unless you or your work has no security - lets hope not!)

You can set up a VPN that will punch through most firewalls (although not all) quite easily with Hamachi.

[https://secure.logmein.com/products/hamachi/vpn.asp?lang=en](https://secure.logmein.com/products/hamachi/vpn.asp?lang=en)

I use it to secure connections from home to other peoples desktops using VNC.

Ubuntu comes with VNC server installed by default, you configure at : System > Pref > Remote Desktop

All you need then to connect, is an IP connection (which you can setup via Hamachi) and a VNC client (of which there are many - I have one on my iPhone even).

The main VNC server (although allas not the default one with Ubuntu) allows you to connect to it with a web browser with no VNC client installed on the client side.  You can navigate to:

[http://theipaddress:5900](http://theipaddress:5900)

A small Java client is downloaded from the machine acting as a server so you can connect from any java enabled browser. Cool.

---

