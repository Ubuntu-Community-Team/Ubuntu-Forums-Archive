---
title: "bridging through a WiFi- not sharing a WiFi via ethernet port"
date: 2015-01-18
forum: Networking &amp; Wireless
---

### Post by jfaberna on 2015-01-18
I have read a lot of post about sharing a WiFi on one PC to other non-WiFi PC connected to the first via Ethernet.  I don't think that is what I want to do.

I have an embedded headless Celeron PC with both WiFi and RJ45 port.  The WiFi port has a Static IP on my home network and host a tomcat web app server.  At present I can us Firefox to get from any browser in the house on any PC to login to the Celeron PC and run the web apps.  The Celeron PC talks to a micro controller system via the ethernet port with Static IP.  There's a telnet port and a primitive web page for configuration of that micro, but I can only use those ports from the Celeron PC.

What I want to do for debugging and testing is to have any PC on the local net use the Celeron PC's access to the micro to look at the telnet and web page of the micro.  Not sure if it's possible.

not sure bridging is the answer. maybe write a web app for the tomcat server than can pass access to telnet and web page.

My backup plan is to just haul a monitor, keyboard, mouse to the Celeron PC, then install a GUI on the Celeron PC.  It's running Ubuntu 14.04 Server, no GUI.

[IMG]http://i62.tinypic.com/2q9fach.jpg[/IMG]

---

### Post by jfaberna on 2015-01-19
A possible workaround that I come up with that would work in my case is the following:  

Since I have Openssh on the Celeron PC, I can login to that box and then use telnet to talk to the Stoker Micro.  I can also use the text based browser, Lynx, to look at the micro's simple web page.  Not perfect but doable.

---

