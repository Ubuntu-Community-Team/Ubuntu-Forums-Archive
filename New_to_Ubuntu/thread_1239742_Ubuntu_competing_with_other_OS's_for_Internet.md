---
title: "Ubuntu competing with other OS's for Internet"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by niallabrown on 2009-08-13
Does anyone know why Ubuntu competes with other computers on a wireless network?  First my Ubuntu machine is working great then I go on my windows machine and it has no internet.  I rest it then the reverse happens.  My Mac is worse it wont run if you have been on any other computers internet connection including Windows.  I know this is not specific just to Ubuntu but I hope someone will know whats going on.

I have:
1 desktop Ubuntu Gnome Ethernet
1 desktop windows Ethernet
1 Laptop Windows Wireless
1 laptop Ubuntu Gnome Wireless
1 Laptop Kbuntu KDE4 Wireless
1 Mac OSX Wireless

The windows machines don't compete with each other and an ubuntu and windows mix with Ethernet don't compete.these wireless machines together that I get a problem.  However does effect the Ethernet machines they can kick off or be kicked off from the wireless ubuntu machines.

As you may guess the computers play an important business function so PLEASE I NEED YOUR HELP!

---

### Post by lswb on 2009-08-13
I really don't understand what you are saying here. What does "compete" mean in this context? What does "kicked off" mean? 

Is it possible you have your lan set up for static ip addresses and have assigned the same address to different machines? Do all the machines have unique host names?

---

### Post by bboston7 on 2009-08-13
Does your wireless router have a configuration file you could post?

Your question is confusing at best...

---

### Post by DGortze380 on 2009-08-13
> **niallabrown said:**
> Does anyone know why Ubuntu competes with other computers on a wireless network?  First my Ubuntu machine is working great then I go on my windows machine and it has no internet.  I rest it then the reverse happens.  My Mac is worse it wont run if you have been on any other computers internet connection including Windows.  I know this is not specific just to Ubuntu but I hope someone will know whats going on.

I have:
1 desktop Ubuntu Gnome Ethernet
1 desktop windows Ethernet
1 Laptop Windows Wireless
1 laptop Ubuntu Gnome Wireless
1 Laptop Kbuntu KDE4 Wireless
1 Mac OSX Wireless

The windows machines don't compete with each other and an ubuntu and windows mix with Ethernet don't compete.these wireless machines together that I get a problem.  However does effect the Ethernet machines they can kick off or be kicked off from the wireless ubuntu machines.

As you may guess the computers play an important business function so PLEASE I NEED YOUR HELP!

Sounds like an issue with your router. 
You're getting some kind of a conflict, IP, DHCP, ARP ...
What router are you using?
Post any config information available.

---

### Post by cariboo on 2009-08-13
Just to add to what the others have said, you don't seem to have dhcp set up properly on you router. Your computers are probably getting the same ip address, set your router to dispense at least 10, if not more ip addresses.

---

### Post by desperado665 on 2009-08-13
Also, if you only have a 4 port router, you will only be able to get 4 clients (wired, wireless or any combination totaling 4). With your configuration, you should probably have at least an 8 port router.

---

### Post by DGortze380 on 2009-08-14
> **desperado665 said:**
> Also, if you only have a 4 port router, you will only be able to get 4 clients (wired, wireless or any combination totaling 4). With your configuration, you should probably have at least an 8 port router.

Not necessarily true...

---

### Post by niallabrown on 2009-08-17
I didn't set-up the router originally but I did find the info to get to the configuration webpage.  It is a Link-sys router.  On the basic configuration page it refers to DHCP server (no idea what that means) but it does say Maximum number of DHCP users and it's set to 4.  Is that the problem?  Do I need the same number as the maximum number of machines I run overall?  Do I add in iPhones and Android phones also if they are set to link to the wi-fi?

> Also, if you only have a 4 port router, you will only be able to get 4 clients (wired, wireless or any combination totaling 4). With your configuration, you should probably have at least an 8 port router.
The router does have 4 Ethernet ports now that I look at it. I assumed the wireless was different from the ports.  Does this mean I need a router with more ports?

> What does "compete" mean in this context? What does "kicked off" mean? 
By kick off I mean that if I unplug the router and plug it back in then start to use say my wired windows desktop, when I go to my Ubuntu machine it wont work. I get a cannot find page error even if the router is still showing a wi-fi connection to the network.  If I went to the Ubuntu one first it would have worked.  The wired connections are more resilient but even they can sometimes stop working when I spend a lot of time on a wireless Ubunut or Mac connection.

---

### Post by Poincare101 on 2009-08-17
> **desperado665 said:**
> Also, if you only have a 4 port router, you will only be able to get 4 clients (wired, wireless or any combination totaling 4). With your configuration, you should probably have at least an 8 port router.

That information is just plain crap. For wired connections, yes you would need 4 ports. But, for wireless you can have as many connections as you want as long as the firmware allows it.

---

### Post by niallabrown on 2009-08-17
So it is a good idea for me to bump the 4 DHCP users to 6 or 8 even?  I cant mess anything up by doing that can I?

---

### Post by nandemonai on 2009-08-17
> **niallabrown said:**
> So it is a good idea for me to bump the 4 DHCP users to 6 or 8 even?  I cant mess anything up by doing that can I?

I'd go 10 to allow for expansion. And no, adding more DHCP leases wont mess anything up, in fact, it will fix your problem ;)

---

### Post by mcduck on 2009-08-17
> **niallabrown said:**
> So it is a good idea for me to bump the 4 DHCP users to 6 or 8 even?  I cant mess anything up by doing that can I?

Not just a good idea, it's what you *must* do to get more than 4 machines connected at the same time. :)

DHCP server on the router is giving IP addresses for your computers. If the router is set to give only 4 addresses, then you only get 4 computers with working network connection. If you want 8 computers (or any other devices) to be able to connect at the same thime, then the DHCP server must give at least that many IP addresses as well. And like nandemonai said, setting the router to allow more connections than what you need is not going to cause any problems so be sure to set it high enough for your needs..

---

### Post by Saghaulor on 2009-08-17
> **desperado665 said:**
> Also, if you only have a 4 port router, you will only be able to get 4 clients (wired, wireless or any combination totaling 4). With your configuration, you should probably have at least an 8 port router.

If the router is configured to distribute x many addresses, x is how many devices that can connect to it without address conflict, the limit of x being 255 including the router on a subnetwork. 

Four physical ports merely limit you to four patch cables, you could plug in four switches and multiple the number of available wired ports/addresses exponentially.

---

### Post by zerhacke on 2009-08-17
One more vote that a router can do more than 4 IP leases no matter how many Ethernet ports there are.

---

### Post by Saghaulor on 2009-08-17
> **niallabrown said:**
> I didn't set-up the router originally but I did find the info to get to the configuration webpage.  It is a Link-sys router.  On the basic configuration page it refers to DHCP server (no idea what that means) but it does say Maximum number of DHCP users and it's set to 4.  Is that the problem?  Do I need the same number as the maximum number of machines I run overall?  Do I add in iPhones and Android phones also if they are set to link to the wi-fi?


The router does have 4 Ethernet ports now that I look at it. I assumed the wireless was different from the ports.  Does this mean I need a router with more ports?


By kick off I mean that if I unplug the router and plug it back in then start to use say my wired windows desktop, when I go to my Ubuntu machine it wont work. I get a cannot find page error even if the router is still showing a wi-fi connection to the network.  If I went to the Ubuntu one first it would have worked.  The wired connections are more resilient but even they can sometimes stop working when I spend a lot of time on a wireless Ubunut or Mac connection.

Wired and wireless connections are limited to the amount of available tcp/ip addresses. Both wired and wireless connections use tcp/ip address to connect on your network. Please see above post.

Using the term "port" is sort of misleading. Those are RJ-45 ethernet jacks. A communication port is something entirely different.

---

### Post by niallabrown on 2009-08-17
Thanks for all the replies!  I set it to 10 as the limit so hopefully all will go well.  So far so good.

---

### Post by nandemonai on 2009-08-18
> **Saghaulor said:**
> If the router is configured to distribute x many addresses, x is how many devices that can connect to it without address conflict, the limit of x being 255 including the router on a subnetwork. 

Four physical ports merely limit you to four patch cables, you could plug in four switches and multiple the number of available wired ports/addresses exponentially.

255-2

One for network address and one for broadcast. I'm sure you know this (based on the nice explanation) but figured I'd point it out for those who don't :)

---

### Post by nandemonai on 2009-08-18
> **niallabrown said:**
> Thanks for all the replies!  I set it to 10 as the limit so hopefully all will go well.  So far so good.

Glad you got it working properly. For a great explanation on IP see:

[http://en.wikipedia.org/wiki/IP_address](http://en.wikipedia.org/wiki/IP_address)

and

[http://en.wikipedia.org/wiki/Internet_Protocol_Suite](http://en.wikipedia.org/wiki/Internet_Protocol_Suite)

Enjoy!

---

