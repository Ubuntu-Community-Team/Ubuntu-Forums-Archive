---
title: "connecting to dsl through router"
date: 2004-12-23
forum: Networking &amp; Wireless
---

### Post by G.I.Josh on 2004-12-23
I'm on a lan.  I connect to a router that connects to the Verizon DSL modem.   DHCP got the ip from the router fine, but the problems arise with pppoeconf.

Actually running pppoe conf, everything went well.  I clicked the default yes for everything and put in the username and password.  It asked if I wanted to start up pppd, so I said yes. 

However, I have no 'net access.  Since I'm going through a router, should I be going with something other then the defaults?  Should it start up something other then pppd?  Why is it not working properly?

Thank you very much for your time,
Josh

---

### Post by az on 2004-12-23
The router should be using pppoe to connect to dsl.  _You_ connect to the router with dhcp.

Can you configure the router to do pppoe or do you need some windows tools?

---

### Post by G.I.Josh on 2004-12-23
I don't have access to the router like that, but I do believe it's already configured to use pppoe.  (It's my uncle's network.)

On Windows, my connection is configured like this (uncle configured it, not me)

Under Network Connections, it has local area connection using dhcp to connect to the router as you said.  Then under broadband, it has verizon.  It's properties shows it as being pppoe.  When I click on it, it asks me my uname and pw.  (well, my uncle's)  Then logs in.

We're only going to be here at my aunt 'n' uncles for about a month, and then it's back to good ol' easy cable.  But I don't want to have to wait for then to  have 'net access on Ubuntu.

---

### Post by randy on 2004-12-24
You definitely don't need pppoe to connect to the router then.  Just setup your network using dhcp

---

### Post by G.I.Josh on 2004-12-24
I've already connected to the router using DHCP just fine.  I just need to tell it to dial in from here.

---

### Post by hardcandy on 2004-12-24
A DSL modem/router should always be connected to the ISP server unless it is unplugged. 
If you can not connect from your computer to the internet, it is because the router/modem is not letting you through. 
If you can connect to the router/modem your network card address may not be allowed to connect due to the router settings. You will need to have access to the router set-up page to enable this.

---

### Post by G.I.Josh on 2004-12-24
I did connect to the router (ifconfig checked out), but my nic address seems to work fine on Windows, so now the whole mess with it has me confused.  I suppose I'll just wait a month 'till I'll be back at home on a nice simple cable connection. ;)

---

### Post by mistic on 2004-12-25
you can try to access your router with your browser (firefox probably), just try surfing to the IP of the router 

just use the command "route" to find out what that IP is...

```
root@iBookLnX:/home/mistic # route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         _**192.168.0.1**_     0.0.0.0         UG    0      0        0 eth0
```

and then surf to it 

[http://192.168.0.1](http://192.168.0.1) (in my case)

---

### Post by jadm5000 on 2004-12-27
okay im baffled - i JUST installed and am also on Verizon dsl and everything zipped by me no sweat, i wasnt even asked anything regarding network, connection ect ( i saw it detected everything as the screen was "flying" by me during installation).
weird.

---

### Post by pontiff778 on 2007-05-15
> **randy said:**
> You definitely don't need pppoe to connect to the router then.  Just setup your network using dhcp


[biology photosynthesis physics Rewards Cards Equity Line Credit](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

### Post by str8line on 2007-08-23
What part of US are you located (North East US or Southern US-West Coast)

---

