---
title: "Ethernet &amp; Wireless on HP Compaq 6715s"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by xcitu on 2008-06-17
Hey.
I have installed Ubuntu 8.04 LTS on a HP Compaq 6715s, but cant get the internet working, neither with cabel or wireless. 
So what to do? 
I did a hardware test and figured out the full name(?) of my network card. 
Here it is:
"Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)"

I also did a lspci:
[IMG]http://i29.tinypic.com/34pggux.png[/IMG]

So what can I do to get my internet working? 
And please do post in noob language, this is the very first time I am using Ubuntu, and only know some basic commands in Terminal :P

I am thankful for every bit of help :)

- X

---

### Post by WSmart on 2008-06-17
If you have a router, click on the double computer display icon on the menu panel and choose manual configuration. Then select the connection and hit the properties button.  You probably need DHCP on that drop down, if you have a router.

I had trouble getting my internet to work on my first Ubuntu install.  And I've had trouble here and there with difference systems since then. I have one network card that I couldn't get to work, and two others that do.

You might also check your router configuration, the web interface.

---

### Post by xcitu on 2008-06-17
Hmm, ok. 
I have tried to put it to DCHP but it didnt work. 

But router, I think I have :P

Its set up like this:
Internet "deliverer"
One main box in our house
Cabel go to one other box.
Cabel from box to "point in wall" in my room
Cabel from "point in wall" to my PC. 

And the other stuff, can you explain howto? I really hate configurating internet, cant stand it :P So I'd be happy with a step to step guide:)

---

### Post by WSmart on 2008-06-17
Cable or DSL usually does have a router, but that sounds wrong, a cable going from the wall to the computer?  

		I bet you can get it going if you play with the manual settings, but if that card isn't supported or isn't working, forget it.  There's also another post here asking for some 'very good help' or something like that;  8.04 is having some very specific network connection issues that appear to be card specific.

		When I moved to Ubuntu I built a new computer and connected it to my old XP machine via a cheap KVM switch.  I already know how to use Windows and I did pay for the damn software, so I don't feel bad about using it.  The advantage is that I lost nothing to move to Ubuntu.  I still had the same system I'd been using for years, so it was more of a lateral move rather then learning everything over again from square one.  But I think it took me eight hours to get the internet connected, the first time.  What finally got me connected was changing the Ethernet cable, even though the cable I'd been using was not bad-I swapped the one I had on the XP system.  All the head aches and it came down to something like that.  So much of working on computers is like solving math problems where it's not so much what you know but how you execute, doing the simple  math correctly.

---

### Post by xcitu on 2008-06-17
Yes, thats correct, cabel from wall. If its helps anything, then I'll let you know that I have fibernet. With it you get 1 main box and several other small boxes to split the internet to different roms/pc's. 
But I'll have a look at it, see if my card doesnt support ubuntu..

If anyone has anything else to say, say it :)

---

### Post by asbjotve on 2008-06-17
It has nothing with router or cable to do.. I have tried in Nomade-modus, DHCP and static IP and nothing works. I get all up and working with Gutsy (Ubuntu 7.10) but have trouble with 8.04.

---

### Post by onegreenparker on 2008-06-17
I used [this](http://ubuntuforums.org/showthread.php?t=767372&highlight=6715s) thread and got the wireless done.
My wired network was fine from day one, only thing I can think of is to try giving your machine a static IP.

---

### Post by xcitu on 2008-06-17
> **onegreenparker said:**
> I used [this](http://ubuntuforums.org/showthread.php?t=767372&highlight=6715s) thread and got the wireless done.
My wired network was fine from day one, only thing I can think of is to try giving your machine a static IP.

And how do I add a static IP?

---

### Post by chili555 on 2008-06-17
If you have the availability of wired ethernet, then that's what you should prefer. It's usually faster and easier than wireless. Make sure you have manual configuration on and roaming off in the double computer display icon on the menu panel. Then open a terminal (Applications->Accessories->Terminal) and do:```
sudo ifconfig eth0 up
sudo dhclient eth0
```Did you connect, that is did you get an IP address, like this:> Listening on LPF/eth0/00:19:d2:c2:1b:8d
Sending on   LPF/eth0/00:19:d2:c2:1b:8d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.1.102 from 192.168.1.1
DHCPREQUEST of 192.168.1.102 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.102 from 192.168.1.1
bound to 192.168.1.102 -- renewal in 37984 seconds.If so, we can make this permanent and automatic.

---

