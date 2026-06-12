---
title: "Shopping for Wireless Router: a couple question"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by bg1256 on 2007-08-17
I'm in the market for a wireless router, but I've never purchased one or even set up my own router in the past...

Here's a brief description of my scenario:

I'll be living in a dorm / apartment building and I will have my own ethernet port.  The connection is high speed and quite fast, actually. The IT department has okay'd my use of wifi, and they can offer support for Windows, but not Linus.

Here are my questions:

I dual boot Windows and Linux.  Which should I use to set up the router?

Second, I am having difficulty ascertaining the difference between a wireless router and a wireless *firewall* router.  Is there one, or does it simply describe software packaged with the router?

Third, are there any particular brands that should be avoided or preferred? 

Thank you sincerely for the help.

---

### Post by lsmobrian on 2007-08-17
The administration of the router is done through a website interface, usually [http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1](http://192.168.1.1)  (depending on your ip address) so if your wireless card works in windows or ubuntu then it doesnt matter which OS you use to setup the router. you will want to be wired to the router for the initial setup

you are in the market for a wireless router not a firewall router, firewall router doesnt include wireless support just LAN.  wireless routers usually include some type of firewall if you are needing one

I dont think brand names for routers matter too much, just make sure it supports your wireless card type (a/b/g/n) and encryption like WPA (if you are in a dorm, it is usually a requirement to use some type of encryption)

---

### Post by CyberBob on 2007-08-17
Setting up a router can be done in either Windows or Linux, as it is simply a matter of starting a browser and entering an IP address something like this: 

 ```
http://192.168.1.1
```

... and then typically a pop-up window appears in which you enter a user id and password to access the router's built-in *firmware *to adjust the settings, including a firewall.  The default username and password are given in the user manual to do this.  I'd advise you to go through the set-up as it is described in the router user manual that comes with it and you should have no problem.

There are routers that have no wireless capability (becoming rare these days) and those that have wireless capability (that have one or more antennas that swivel around the case).  Both types have a firewall capability to provide a layer of security between the internet access point and your computer.  Instructions for setting up the firewall are usually included in the user manual too.

I currently use a Netgear router at home, and just two days ago helped my sister set up a Linksys router at her home.  We did both with Ubuntu even though the routers both came with a "Windows" CD and the packaging lists various versions of Windows as system requirements.  They are not required at all.

Having said that, if you feel more comfortable doing the router setup with Windows in your dual boot system, by all means go ahead and do that.  You will still be able to access the wireless router with Ubuntu or whatever you are using ... as long as the wireless hardware works.  That is another story ...

Good Luck!

---

### Post by bg1256 on 2007-08-17
Thanks for your replies.

My wifi driver works in Ubuntu, after installing ndiswrapper and then the proper driver.

So, if I'm understanding you right, a wireless *firewall* router only lets me connect to other devices wireless, and not the internet?

---

### Post by sci-fi guy on 2007-08-17
Actually, I think that a firewall router just acts as a hardware firewall (no software to install) as well as a router. I may be wrong though...

EDIT: Did that make sense to anyone? I don't even get it anymore.

---

### Post by bg1256 on 2007-08-17
If that's true, would that be good or bad in terms of Linux usage?

---

### Post by TheTinman on 2007-08-19
What sci-fi guy was saying kind of makes sense.  My understanding is that wireless routers have an inherent firewall.  In other words, they add another layer of networking protection (i.e. in addition to a software firewall, such as Ubuntu's, which Firestarter serves as the GUI to).

> If that's true, would that be good or bad in terms of Linux usage?

It has no bearing on Linux (or any other OS) in particular.  Having a router between your machine and the Internet is great in that the router can be configured to add protection.  Where it might get confusing, though, is when applications are run on your machine with the router between the machine and the Internet.  

As a general example, take bittorrent applications.  Whereas before (with no router in place) you would simply launch the program and go to work, now you will have to (pretty easily) configure the router to allow bittorrent traffic to go where it needs to.

Expanding on the bittorrent example.  Let's say you are using Azureus, and your incoming bittorrent port (which you could check by looking at the Azureus settings/preferences) is 25277.  With no router in place (which means you just have a software firewall, possibly) everything is "fine."  With a router in place, however, the router has to know how to get that bittorrent traffic to your machine through port 25277. This doesn't seem like a big deal if you only have one computer using the router, but it becomes especially important if there are multiple machines in your room making use of your single router.

I hope this made sense, and let me know if you need further explanation.  As those other people said, brand won't matter much.

(ps--I now see that there was a discussion about a "firewall router" as a specific device--I didn't realize that as I typed my thing)

---

### Post by bg1256 on 2007-08-19
Thanks for your post, Tinman. 

I actually purchased a router from tiger direct last night.

I may need some help getting it configured, and I'll post here if I get stuck.

---

### Post by TheTinman on 2007-08-19
No problem.  Post back here when you get it and we'll help you.


:guitar:

:lolflag:

:popcorn:


(added for effect)

---

