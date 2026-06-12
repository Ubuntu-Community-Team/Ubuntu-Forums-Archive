---
title: "Ubuntu box as a Router"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by SysFail on 2007-06-02
I already have my ubuntu LAMP server setup as a router and it works amazingly well...however...

Does anybody know of any software etc that will give me much better monitoring capabilities of what the traffic on that box is doing??

It sits under my desk headless ( I use it for a footstool actually hahah) 

I want to be able to watch the traffic from my LAN going through it in realtime or something cool like that, as well as be able to see who is trying to access the box by ssh or other ports etc etc

I know I can ssh in and sit and read the log files, but there must be a cooler way than that to do these things??  Some kinda web interface maybe??

LAN is 6 PCs plus a netgear for wireless access and a Cisco 3550 switch...


Any help is appreciated!
Thanks!
SysFail

:D

---

### Post by handydan918 on 2007-06-02
Umm, this may not be what you're looking for, but ethereal (or another packet sniffer) may do what you want. Not sure if webmin has this kind of capability....:confused

---

### Post by seanp2k on 2007-06-02
[http://www.pfsense.com/](http://www.pfsense.com/)

Configure just like a router with a web interface, view graphs and stats in realtime with your browser, etc.  Will run off of a LiveCD if you so desire.  Stupid easy to configure.  Seeing as how you have a cisco router up and running you should have zero problems.

Here is a list of the packages it comes with:
[http://en.wikipedia.org/wiki/PfSense#Packages](http://en.wikipedia.org/wiki/PfSense#Packages)

Maybe you could try installing and configuring all of those.

---

### Post by SysFail on 2007-06-03
Thanks for the help guys...trying both suggestions now

---

