---
title: "\Where's my desktop?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Yancyd67 on 2009-12-06
New dummy post!!  Spent last three days trying to load Ubuntu Server on new hardware.  After many frustrating hours things seem to load and I thought I was done.  But how do I get to some semblance of a desktop as I cannot get out of what I think of as a dos command window where I can enter my user name and password but from there nothing prompts me to desktop.  Please be kind as I indicated I am a software/OS dummy.

---

### Post by lisati on 2009-12-06
The server edition doesn't install a desktop by default. If you really want one, you can login and use something like the following:
```
sudo apt-get install ubuntu-desktop
startx
```

---

### Post by Paqman on 2009-12-06
You'll get a lot of stuff in ubuntu-desktop that you might not want. For example, Open Office is a massive download and no use at all on a server.

To install a more minimal (but very usable) desktop you could instead try:
```
sudo apt-get update && sudo apt-get install gdm xorg gnome-core indicator-session-applet update-manager gnome-themes network-manager gdebi
```

Further packages you require (eg: webmin?) can be installed through System > Admin > Synaptic.

---

### Post by blazemore on 2009-12-06
Why are you installing Ubuntu server if you want a desktop system? I don't understand.

---

### Post by Yancyd67 on 2009-12-06
blazemore,  You missed the important part of my post which is "I am a dummy" and trying to learn how to set up a server.  I don't even know what a server is but I would like to do one for a web site without have to pay for hosting, plus I may get a little bit smarter.  So you may see more novice questions coming from me and I hope will understand and help
Thanks to all.

---

### Post by D3M0L1$H3® on 2009-12-06
> **blazemore said:**
> Why are you installing Ubuntu server if you want a desktop system? I don't understand.

There's nothing wrong with wanting a GUI. Most people now are more comfortable using the desktop interface to manage their server, than trying to do everything from a terminal.

---

### Post by Paqman on 2009-12-06
> **blazemore said:**
> Why are you installing Ubuntu server if you want a desktop system? I don't understand.

It could be a web dev box, or maybe they just want to have a familiar environment while they're learning about servers.

---

### Post by mickie.kext on 2009-12-06
> **Yancyd67 said:**
> blazemore,  You missed the important part of my post which is "I am a dummy" and trying to learn how to set up a server.  I don't even know what a server is but I would like to do one for a web site without have to pay for hosting, plus I may get a little bit smarter.  So you may see more novice questions coming from me and I hope will understand and help
Thanks to all.


You do not need to install Ubuntu Server to actualy run a server. You can go with plane desktop edition and than install server apps, like Apache, MySQL, PHP... or just install LAMP which is a bundle off all that. 

Ubuntu Server comes without desktop environment because you usually do not need desktop (which uses server's hardware resouces) on server if you know all of terminal commands needed.

---

### Post by Paqman on 2009-12-06
> **Yancyd67 said:**
> I don't even know what a server is but I would like to do one for a web site without have to pay for hosting, plus I may get a little bit smarter.

Fair enough. You're probably on a dynamic IP though, which means you'll need a service like [DynDNS]("http://www.dyndns.com/") to make your machine accessible to folks outside your network.

A word of warning though: a web-facing server is at a real risk of being hacked if you don't know how to secure it. Read up on server security.

---

### Post by Yancyd67 on 2009-12-06
So Mickie, just so I understand, you are saying that I can run the standard desktop version of ubuntu and then add Apache, MySQL, PHP and/or LAMP and this will give me a user friendly, i.e., Windows or Mac type desktop interface.  If that is correct, I thank you and I love it.

---

### Post by Paqman on 2009-12-06
> **Yancyd67 said:**
> So Mickie, just so I understand, you are saying that I can run the standard desktop version of ubuntu and then add Apache, MySQL, PHP and/or LAMP and this will give me a user friendly, i.e., Windows or Mac type desktop interface.  If that is correct, I thank you and I love it.

Sure. 

LAMP = Linux+Apache+MySQL+PHP, which is a very popular way to set up a server. If you install the package lamp onto desktop Ubuntu it turns it into a server. Likewise you can install the desktop packages on the server version. 

There's a bit more under the hood going to that differentiates the two, but you get the general idea. Same system, two different default setups.

---

### Post by YancyD on 2009-12-07
Thanks Paqman, I definitely plan on studying security.

---

### Post by mickie.kext on 2009-12-07
Yeah, just like Paqman said. You can run LAMP or you can install and configure Apache, MySQL and PHP separetly. You can do that on either Desktop or Server Edition of Ubuntu. Or BSD flavour, you can do it even on Windows (aldo I do not recommend it because you will get hacked daily). 

Most eficient choice will be Unix-like OS (ie linux distro, BSD variant or Solaris) and Apache, MySQL and PHP configured separetly, not bundle like LAMP. Given that you know how to do that. But for starter you can start learning with LAMP and desktop linux, you can't become expert over night.

---

### Post by YancyD on 2009-12-07
Paqman, I tried: sudo apt-get update && sudo apt-get install gdm xorg gnome-core indicator-session-applet update-manager gnome-themes network-manager gdebi

but got error E: Couldn't find package indicator-session-applet.  

Thanks

---

