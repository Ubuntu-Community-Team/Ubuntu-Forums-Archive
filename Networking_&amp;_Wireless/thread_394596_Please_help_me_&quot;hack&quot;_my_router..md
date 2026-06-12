---
title: "Please help me &quot;hack&quot; my router."
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by frup on 2007-03-27
I've just spent about 3 hours trying to make my home IP go to my main computers apache server. I have tried so many different things and none of them seem to work and all I can think of is that my router needs manual editing. I can't SSH or Telnet in to it...

my router is a conexant hasbani model of some sort... I don't know anything else about it... I tried looking through my manual CD, through all of its config pages on 10.0.0.2 and on its self. this its firmware etc.
Firmware Version:	ETHADSL_USB_080902_REL9
Customer Software Version:	080902_REL9-MR1


I have set it to port foward (under virtual servers) port 80 to my main computer 10.0.0.4, this is under TCP and UDP and looks like so
ID    	 Public Port   	 Private Port   	 Port Type   	 Host IP Address
5 	 80 	 80 	TCP 	 10.0.0.4 	
6 	80 	80 	UDP 	10.0.0.4

Under its misc config I have made:

HTTP server access
     All

(i had this on LAN which blocks http access as default it goes to the 10.0.0.2 admin gateway... its still doing this with port 80 forwarded)

I changed this too

DMZ 		[Enabled]
DMZ HOST IP 		[10.0.0.4]


What else do I need to do!!! please :)

I searched for my firmware/for conexant hasbani routers for everything on google... i've tried ssh and telnet (connection refused) so unless theres another option i need to know how i can break its security and change what I want (And yes i know its easier said than done).

---

### Post by kidders on 2007-03-27
Hi there,

You would do this the same way, regardless of your router or OS...

[LIST]
[*]Disable remote access to any HTTP-based configurator (which would obviosuly clash).
[*]Forward port 80 to the right internal IP (which you seem to have done).
[*]Make sure port 80 is open on the target machine.
[/LIST]

> I have tried so many different things and none of them seem to workWhat's going wrong, exactly?

---

### Post by HereInOz on 2007-03-27
Silly question perhaps, but have you opened port 80 for inbound in the firewall on the machine running the apache server?

---

### Post by Austin_KW on 2007-03-27
Don't know this router but I suggest that you either port forward(specific ports) or DMZ(everything) not both. Also the misc config option for http server access, not sure what this is but it may trap access to port 80 and not pass it through your router.

---

### Post by didijeeeke on 2007-03-27
> **frup said:**
> 

HTTP server access
     All



try disabling this for the Internet side i think they mean your router http config page not sure.

---

### Post by mosimo on 2007-03-27
Is the problem that when you try and access your external IP you get your routers page? If so then It could be the same problem I had. I forwarded port 80 to my machine, how ever when I tried my IP it always went yo my router setup page. 
The problem I found out was that If you just try and access your external IP it never makes it out on to the internet and back again to get forwarded to port 80 on your computer. If I got someone else to connect ot my external Ip however... it worked perfect and the apache server worked fine. 
The router basically goes "x.x.x.x? thats your IP you ninny" and sends you to the router as its internal admin setup port is set at 80 no matter what, changing or disabling remote access still allowed you to access it internally.

Rambled on a bit but just try your IP from another connection outside your internal network and see if it works :P

---

