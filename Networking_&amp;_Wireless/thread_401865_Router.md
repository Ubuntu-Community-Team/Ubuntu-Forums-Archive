---
title: "Router"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by morequarky on 2007-04-05
Questions:
What software do I need to use install on ubuntu to make a router?  Any suggestions?
What kind of termination do I need to use to connect my computers to my router?(regular patch or cross)
Can my router also be a print server?

What I am doing:
I am trying to make a new network from my spare box, currently running xubuntu, will reinstall.  I don't know what software I should use to route with.  Also, I don't know if regular patch cable will work or do I need cross-cables to connect my computers to the network cards in the router. I have two printers.  I would like to connect them to the router and have the router server the printers to the other computer in the network.  I want to connect my current router(linksys) to my new router in such a way that the linksys doesn't create a new network and my router can control the wireless accesses, if that isn't possible, I worry that the wirelessly connected computers won't be able to use the print server that is in another network.

What I have:
TinyXP 32bit laptop
Apple - Mac OS X (ppc) laptop
WinPro64/XP32/Ubuntu64 Tri-booting desktop
And a PC133 RAM Xubuntu Box I am to receive soon, and make the router out of it.
Linksys router/internet enabled.
Samsung Laser jet printer
HP deskjet

Thanks for any help.  Ubuntu, Linux, and ubuntuforums.org are fantastic.

---

### Post by Soarer on 2007-04-05
You have asked a simple question, but the answer is potentially rather complex. Essentially you can edit a lot of configuration files, or you can install a GUI to do it for you.

I haven't used it, but the simplest GUI is said to be [Firestarter]("http://www.fs-security.com") - it's in the repos and that link has a lot of information about how to use it to do what you want.

I use [Shoreline Firewall (often called Shorewall)]("http://www.shorewall.net") which MAY be more complex, but is very flexible. Lots of information on that site too. It is also in the repos, but I downloaded it to get the latest, I think.

Oh, and I would install Unbuntu Server on that box, and configure the other stuff with [Webmin]("http://www.webmin.com") which is no longer in the repos but has a .deb available. You control Webmin (and therefore the server) via a web interface from your client PC so the server doesn't need a Gnome or KDE desktop installed.

[EDIT] and the server will need at least 2 network cards, one for the Internet side (to your Linksys) and one for your internal network connection

---

### Post by morequarky on 2007-04-05
> **Soarer said:**
> You have asked a simple question, but the answer is potentially rather complex. Essentially you can edit a lot of configuration files, or you can install a GUI to do it for you.

I haven't used it, but the simplest GUI is said to be [Firestarter]("http://www.fs-security.com") - it's in the repos and that link has a lot of information about how to use it to do what you want.

I use [Shoreline Firewall (often called Shorewall)]("http://www.shorewall.net") which MAY be more complex, but is very flexible. Lots of information on that site too. It is also in the repos, but I downloaded it to get the latest, I think.

Oh, and I would install Unbuntu Server on that box, and configure the other stuff with [Webmin]("http://www.webmin.com") which is no longer in the repos but has a .deb available. You control Webmin (and therefore the server) via a web interface from your client PC so the server doesn't need a Gnome or KDE desktop installed.

[EDIT] and the server will need at least 2 network cards, one for the Internet side (to your Linksys) and one for your internal network connection


Thanks for the helpful info.

Just to be clear, I want to replace my linksys router and do all routing through my new ubuntu server router.  The linksys would be downgraded to only supply wireless access to the network controlled by my new ubuntu router.

---

### Post by morequarky on 2007-04-05
Has anyone tried ZEBRA?

---

### Post by coxy on 2007-04-05
Have you looked into Smooth Wall?

[http://www.smoothwall.org/](http://www.smoothwall.org/)

---

### Post by Soarer on 2007-04-05
> **morequarky said:**
> Thanks for the helpful info.

Just to be clear, I want to replace my linksys router and do all routing through my new ubuntu server router.  The linksys would be downgraded to only supply wireless access to the network controlled by my new ubuntu router.

OK - I am not sure you can do that. You would need to route the wireless clients' requests out of the Linksys, back to the Ubuntu server, through the server then back to the Linksys to get out to the Internet. I would be surprised if this can be done. I can't do it on a Speedtouch wireless router I have, so I don't use the wireless connection on the router (but it can't be turned off, unfortunately). Instead I have a Netgear wireless hub which goes into the server, then the server is connected by wire to the Speedtouch, which is then connected to the Internet.

---

### Post by Soarer on 2007-04-05
> **coxy said:**
> Have you looked into Smooth Wall?

[http://www.smoothwall.org/](http://www.smoothwall.org/)

If I read that site correctly, it seems to turn a PC into a router completely. I am not sure you can do, for example, printer sharing on Smoothwall, as it installs a Linux OS of it's own on the box.

Looks a great system for a dedicated router though.

---

### Post by koenn on 2007-04-05
re OP : 
I think what you're trying to do is possible. However, of you don't know a few basics about netorking, explaining it all via this forum might be quite hard. 

For starters, I find your OP rather confusing - you talk about a PC that you'll turn in to a router, then about a Linksys router. So when you ask "What kind of termination do I need to use to connect my computers to my router?" and "Can my router also be a print server?", which of the 2 routers are you refering to ? 

Also : how many computers are we talking about ? (router-PC not included ?). How many will use the wired network ? How will the wired PC's be plugged in ? using the LAN ports of the Linksys ? Using each a different NIC on the router-PC ? Or do you plan to by a switch ? (the type of cable you need depens on wheter it's a NIC to NIC connection or not)

You don't really need specific software, the linux kernel in itself handles routing. You might need iptables (and eg Firestarter as a GUI frontend to iptables). 

> I want to replace my linksys router and do all routing through my new ubuntu server router. The linksys would be downgraded to only supply wireless access to the network controlled by my new ubuntu router.
Doable. However : how do you connect to the internet ? because you now want the ubuntu pc to connect to your ISP. Making a Linux system connect over ADSL directly is possible (I read a HOWTO once - long time ago) but rather more complicated than just using ethernet to a router/ADSLmodem that handles the tricky parts. 
> 
I worry that the wirelessly connected computers won't be able to use the print server that is in another network.
the linksys can route between the wireless LAN and the (wired) print server so that should be not too much of a problem. 


Like I said, It's going to take some work. Start with outlining the networ(s) as a whole : all pc's and other devices, how they connect to each other, what they should be capable of (eg share internet access ? ... ) and be very precise. 
Then we'll see.

---

### Post by dbott67 on 2007-04-05
Just to add to the part about using the Linksys for wireless.  As koenn points out, it can be done.

Basically, just do the following:[LIST]
[*] Turn off DHCP on the Linksys and let your PC-router handle assigning DHCP, NAT and routing requests
[*]Assign the Linksys a static IP address on the same internal subnet as your PC-router (this way, you will be able to login to the Linksys from any PC on the internal LAN).
[*]Connect the Linksys to your network hub/switch using one of the LAN ports.  [COLOR=Red]**Do NOT use the WAN/INTERNET port on the Linksys.**[/COLOR][/LIST][COLOR=Red][COLOR=Black]By using only the LAN ports on the Linksys and turning off DHCP, you will essentially have turned the Linksys into a wireless switch (no router, no NAT, no firewall, etc.).

-Dave
[/COLOR][/COLOR]

---

### Post by morequarky on 2007-04-05
Great I am getting all the information I need.  You all deserve a metal.

dbott67:  Thanks, I would have had use trial and error to get the linksys to stop routing.
koenn:  Adsl to a ubuntu box like you said would be hard.  Thanks for the heads up.  But, here in Korea, the internet is ethernet, so I shouldn't have a problem using one NIC on my pc-router for Internet.  

My network is very small.  I am talking about connecting three computers to my pc-router.  That is it.  Very small, but very fun/educational.  :D  

Termination.  I have my own Cat5e wire and have recently ran it and terminated it correctly.  It was a patch style connection from the linksys to the desktop.  With the router, I will connect the hopefully four NIC to various items in the network.  NIC to NIC should be a cross-cable if I remember right.  And NIC to linksys should be patch/normal style termination.

I hope to get three cheap gigabit ethernet cards and use them. :D  That will make my desktop connect to the router-pc with gigabit speeds.  Nice but usesless unless I can get a gigabit adapter for the laptops to also connect using gigabit.

Again I need to read up on print servers.  I want to router to be my print server.  I have heard and had trouble sharing a printer from ubuntu to windows using cups.  I hope I can connect my two printers to the router and make it a print server so ubuntu/mac/win has no problem printing.  At least that is the goal.  I have to read up on that.

Small fun/education network.  :D

Thanks again.  Been great.

---

### Post by koenn on 2007-04-06
Have fun !

---

### Post by morequarky on 2007-04-29
Hi,

Is there a debian router how to somewhere online.  I know linux does static and dynamic routing very easily using various protocols, but I don't know what the commands are or what packages I need to install.

Does server Ubuntu have these packages installed already?  What packages are they and what commands/files need to be used to modify settings?

Too many questions.

Sorry.

Thanks.

---

### Post by morequarky on 2007-04-29
Just want to point out that [URL="http://google.com/coop/cse?cx=000859390548494864150%3Aqm2wpukqlxe"]
This search engine[/URL] works really well.  And found a lot of what I want.

---

### Post by koenn on 2007-04-30
> **morequarky said:**
> Hi,
Is there a debian router how to somewhere online.  I know linux does static and dynamic routing very easily using various protocols, but I don't know what the commands are or what packages I need to install.

Does server Ubuntu have these packages installed already?  What packages are they and what commands/files need to be used to modify settings?
.
[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm) should get you going. 
it's basically routing + iptables. routing is done by the kernel, iptables has to be installed if it is not already there :

```
kn@ix:~$ apt-cache policy iptables
iptables:
  Installed: 1.3.3-2ubuntu4

```

---

