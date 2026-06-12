---
title: "Ventrilo, Static IP address, and port forwarding"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by Tyke91 on 2008-08-31
Hey there. 

system specs
=========
OS - Ubuntu 8.04 
Router - AirLink 101 300N wireless router (ethernet cable, not using wireless on this comp)
Program - Ventrilo Server 3.0
=========

I'm trying to set up a ventrilo server for my friends and I to talk on, but I've run into a little snag... I don't know anything about networking AT ALL!

So... first thing's first... I'm behind a router, so I need to forward all connections coming into the ventrilo port to my computer... but my dad also uses ventrilo. will this screw up his connection?

second... I don't know exactly how to go about forwarding. I know how to get to my routers configuration settings, and I know that the default port for ventrilo is 3784. other than that, I don't know how ports work... does my router have a port 3784, through which all incoming data should flow to my computer? OR does my computer have a port 3784, to which my router should send all incomming data of a certain type?

third... I think that I have set my IP address to a static one, but I'm not sure... is there any way I can tell?

and the last thing... I've tried starting the default server, but I keep getting an error message that says ```
ERROR: Unable to bind to TCP socket.
```
I've no clue what to do... but I think that it is because of my inability to understand port forwarding and how to set a static IP address...


Thanks for reading all the way to the bottom... I know that it is very noobish of me to ask about this sort of thing... but I have no experience in the matter and I am really stuck. I also know that it is in slightly poor forum ettiquite to post so many topics as one thread, but they are all interconnected, and at the end I plan to create a page with a how-to on it so that anyone using google can easily find the exact answer to this predicament instead of having to go through this long process again.

---

### Post by caljohnsmith on 2008-08-31
> **Tyke91 said:**
> 
So... first thing's first... I'm behind a router, so I need to forward all connections coming into the ventrilo port to my computer... but my dad also uses ventrilo. will this screw up his connection?

Yes, it will screw things up, because both you and your Dad can't simultaneously run Ventrilo servers if both your Servers use the same incoming TCP port. But, if your friends can set up their Ventrilo clients (or whatever they are called) to use something other than Ventrilo's default 3784 TCP port you mention, then you could make it work. In other words, when you and your Dad share the same router, you are both sharing the same internet IP address; so if your router gets an incoming request from someone to connect to TCP port 3784, it wouldn't know if it is meant for your Ventrilo server or your Dad's Ventrilo server. 

Bottom line is, unless you can have your friends change their Ventrilo clients to use a different TCP port, and then set your Ventrilo server to use that new port, I think you're stuck.

---

### Post by Tyke91 on 2008-08-31
my dad doesn't run a ventrilo server... just the client. Does that mean it will be ok?

---

### Post by caljohnsmith on 2008-08-31
> **Tyke91 said:**
> my dad doesn't run a ventrilo server... just the client. Does that mean it will be ok?
Sure, I think you should be OK then. :)

And to answer another of your questions, when you got that "ERROR: Unable to bind to TCP socket" error, did you run the server as root (i.e. with sudo)? If you're not running it with sudo, that might be the cause of that error, but I of course can't be sure. Does the documentation say that the server should be run as root? 
[quote=Tyke91]
second... I don't know exactly how to go about forwarding. I know how to get to my routers configuration settings, and I know that the default port for ventrilo is 3784. other than that, I don't know how ports work... does my router have a port 3784, through which all incoming data should flow to my computer? OR does my computer have a port 3784, to which my router should send all incomming data of a certain type?
[/quote]
Yes, the router has a TCP port 3784, and so does your computer. The problem is that since a router uses "network address translation" (NAT) as its means to allow more than one computer to share the same internet address, the router's ports do not correspond directly to your computer's ports. But if you set up the correct port forwarding in your router, then it will correctly route any incoming traffic on port 3784 to your computer's port 3784.
> 
third... I think that I have set my IP address to a static one, but I'm not sure... is there any way I can tell?

Yes, your computer will need to have a static IP address so that the router can always route Ventrilo traffic to your computer.

So the bottom line is, set up a static IP for your computer, and then go into your router's configuration and have it forward TCP port 3784 to your computer's IP address. If you need help with the port-forwarding, check out [www.portforward.com](www.portforward.com) or the manual for your router. Let me know if you need more details/info.

---

### Post by Tyke91 on 2008-08-31
thanks for all your help ^^ I'll keep at it

---

### Post by Iceburgh69 on 2009-10-04
This seemed the most likely thread in which I could ask this. I just switched to the Jaunty Jackalope last night, and I'm trying to set up a vent server. I have no idea how to set up a static IP, or anything like that for port forwarding.
 
Other than that difficulty, and an issue with Wine and WOW, I'm enjoying Ubuntu a lot, and may put it on the rest of my computers.

---

