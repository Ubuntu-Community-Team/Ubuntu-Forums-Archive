---
title: "Ubuntu/winXP network problems"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by mcsix on 2006-10-19
I have searched through the forums for days trying to figure this out. I see many posts with similar situations that don't work for me or that I just don't understand so if this has been answered before I apologize in advance.

I have a desktop that connects to the internet with dialup. That is working fine. The desktop has a Trendnet wireless router connected to the internal network card. 
The router is set at 192.168.1.1. 
I can connect to the internet fine with the modem. 
What I want to do is share the dialup modem connection with other computers in the house wirelessly as well as have some shared folders between the computers. 
This all works fine using winXP on the desktop with the dialup modem connection but when I am running ubuntu I cannot get it to work. 
I have tried using firestarter to enable ICS but with no luck. 
My laptop running xp finds the wlan connection fine and i can even access the router options typing in [http://192.168.1.1](http://192.168.1.1) but I cannot figure out how to share the modem connection. I have tried setting up eth0 (which i assume is my lan card right?) to use dhcp and i have tried setting it to a manual ip of 192.168.0.1 but still no luck. 
Should ubuntu see both the router and the network card? In system/networking it just sees eth0 and ppp0, my network card and my modem. Should it list the router as well? eth1?
I notice on firestarter, when i tried to access the internet on my laptop, that the events tab listed some 168.192... address as an inbound source so i clicked on that event and 'allowed' it but that did not help either. 
What am i missing here? It seems as though I am very close just missing something simple. I don't know if there is something wrong with my setup or firestarter is blocking or what.
Any help is greatly appreciated.
Thanks.
Brian. 
p.s. i am loving ubuntu.  i have been trying different distros for years but never kept using linux, always going back to windows. I think that with ubuntu i am may never go back to windows again.

---

### Post by mcsix on 2006-10-21
Well I have tried about every combination of setting on the router and the laptop that i can think of. Nothing works. I can ping either machine from the other but I just cannot get the internet working on the laptop. So my question is...is there a router out there that will work in this situation? I don't really know that it is a hardware problem or not but I am willing to try a new one.
Should ubuntu see my router? I mean I can access the router through the router's http address but should ubuntu list the router under network connections? My connections only list eth0 and ppp0. My network card and my modem. Do I need a different type of router?

---

### Post by lloyd_b on 2006-10-21
Have you looked at this thread?

[http://www.ubuntuforums.org/showthread.php?t=91370]("http://www.ubuntuforums.org/showthread.php?t=91370")

It's a HowTo document for doing exactly what you're trying to do.

Lloyd B.

---

### Post by mcsix on 2006-10-21
Thank you so much. I don't know how I missed that page. I have been searching for days and trying different things. After reading that page I had it working in minutes. You are a life saver.
Thanks again.
Brian

---

