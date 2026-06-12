---
title: "Ubuntu and firewall routing traffic shaping"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by mccollums on 2007-05-30
Does the ubuntu server or desktop version have the built-in capability to do traffic shaping,  routing ....? 

I've been working with a cisco router to prioritize citrix traffic and have it working pretty well....  would like to try this on linux...  to give me an excuse to play around a little bit.

---

### Post by reckless2k2 on 2007-05-30
Well routing can be done by editing the iptables. This is all similar if you've used the command interface on your cisco router to conf everything. As far as traffic shaping, I can't remember but that is a script that I believe you dump into the iptables as well that prioritizes packets. I know I did this using smoothwall which is a linux firewall program but all is similar because it's all linux. 

Basically, you are going to be digging and editing iptables. And you're going to need to NICs defined on your linux box which will now act as a router/firewall.

---

### Post by mccollums on 2007-05-30
Thanks for the quick response....  so basically this app 

[http://lartc.org/wondershaper/](http://lartc.org/wondershaper/) 

and this site

[http://lartc.org/](http://lartc.org/)  

are all relevant to ubuntu?

---

### Post by reckless2k2 on 2007-05-31
Yeah you're getting the idea. I customized my script to set VOIP at the highest priority and FTP at the lowest. I run a few different servers on different machines and needed to control bandwidth. If you are looking for a firewall/routing solution, I'd suggest using a dedicated product like smoothwall or ipcop. They can both run on dinosaur computers. I ran mine on a 200MHz Pentium I with 128MB of RAM. I like smoothwall a lot because much of it requires hitting the command line for tweaks.

---

