---
title: "About gateway"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by satimis on 2007-01-26
Hi folks,

Ubuntu-6.06.1_LAMP-server-amd64

Connection:
Server --> Router --> Modem --> ISP

The connection to Internet is running fixed/static IP.  I have domain registered.  I suspect the router which was supplied and presetup by ISP on loan, has been locked by ISP.  The internel IP of the server is 192.168.0.10.  IP address 192.168.0.1, LAN, on the router is locked by ISP.  Typing 192.168.0.1 on browser requested login and password.  Typing admin login and password did not work.

Now I'm prepared to build my own gateway including firewall on an old PII box running OpenBSD as OS.  The new connection will be;
Server --> Gateway --> Modem --> ISP

The router will be removed for other use, not necessary going through 2 gateway.

Please advise what information are needed from ISP to setup my own gateway.  What is the reason for ISP to lock IP address 192.168.0.1 on the router which is on my LAN.

TIA


B.R.
satimis

---

### Post by highneko on 2007-01-26
I may be wrong, but maybe your router has a password by default? The default username for my router was "admin" and it didn't have a password. You can check the default username and password here: [http://portforward.com/english/routers/port_triggering/routerindex.htm](http://portforward.com/english/routers/port_triggering/routerindex.htm)

---

### Post by satimis on 2007-01-27
Hi highneko,

Tks for your advice and URL

> 
You can check the default username and password here: [http://portforward.com/english/routers/port_triggering/routerindex.htm](http://portforward.com/english/routers/port_triggering/routerindex.htm)
The router is "Linksys Ethernet/DSL Router"
Model:  BEFSR41v2

Made following test;
- Browsed the above URL
- Clicked "Linksys BEFSR41v2"
- on another page, clicked "1st SMTP Server"
It started "Port Triggering for the Linksys BEFSR41v2"
[http://portforward.com/english/routers/port_triggering/Linksys/BEFSR41v2/1st_SMTP_Server.htm](http://portforward.com/english/routers/port_triggering/Linksys/BEFSR41v2/1st_SMTP_Server.htm)

I can't find MAC address of the router, username and password there.  Please help.  TIA.

Previously I made following test
- removed the Router and connected the server direct to the Modem
- it can ping my static/fixed IP
- if failed to ping URL and IP address of websites on Internet, saying "unrechargebale"


B.R.
satimis

---

### Post by highneko on 2007-01-28
Maybe I gave you the wrong guide. Sorry about that. Try this one to get your password:
[http://portforward.com/english/routers/port_forwarding/Linksys/BEFSR41v2/default.htm](http://portforward.com/english/routers/port_forwarding/Linksys/BEFSR41v2/default.htm)
Here is some more information about your router:
[http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1138057636615](http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1138057636615)

Your username should be blank, and password is admin.

---

### Post by satimis on 2007-01-28
Hi highneko,

Tks for your URL

> 
Try this one to get your password:
[http://portforward.com/english/routers/port_forwarding/Linksys/BEFSR41v2/default.htm](http://portforward.com/english/routers/port_forwarding/Linksys/BEFSR41v2/default.htm)

Under "Do not skip this step!
Please enter the static ip you want to forward to:
192.168.1[       ]"

I don't know what to type here.

The external fixed/static IP is "220.232.213.178"

IP address on the server is "192.168.0.10" to connect ISP

If on browser typing "192.168,1,1, it only hung there and finally time out.

If on browser typing "192.168.0.1", it prompted:-```

"Enter username and password for "Linksys BDFSR41v4 at http://192.168.0.1
User Name [       ]
Password [       ]

```

I have no info to satisfy it.  Username=blank and password=admin did not work.

Others noted with tks.  


B.R.
satimis

---

### Post by RandomJoe on 2007-01-28
To run your own router, since you have a fixed IP provided, all you need are the IP, subnet mask, gateway IP, and DNS server(s).  You may also want NTP server, or other services they provide, but they aren't necessary.  Plug those values into the firewall config files and you're good.  

Of course you will also need to set up a second NIC for the internal LAN side - pick a private IP range (most commonly 192.168.x.x) and you can either use fixed IPs in everything or set up a DHCP server for the LAN interface.  Some distros require explicitly enabling forwarding between the two NICs before any routing occurs, I don't know how BSD defaults.

Most routers default to 192.168.0.x for the IP range they hand out, and the router takes the first IP for itself - no particular reason, it needs one so it grabs that one.  The ISP may feel they can minimize support calls if they keep the thing locked and don't let people play with it.

Personally, I don't use a "router appliance" at all - there's just way too much flexibility in rolling my own with an old computer like you talk about.  I run Linux on mine though, usually Slackware since it's nice and light anyway and I'm so familiar with it.

---

### Post by satimis on 2007-01-28
Hi RandomJoe,

Tks for your advice.

> 
To run your own router, since you have a fixed IP provided, all you need are the IP, subnet mask, gateway IP, and DNS server(s)

fixed IP - I have fixed IP/WAN for external
IP - What IP you are referring?
subnet mask - I have
gateway IP - I don't have ISP's gateway IP
DNS server - I can use ISP's DNS or OpenDNS

I expect finding all necessary info myself, if possible, not to ask ISP.

> 
You may also want NTP server, or other services they provide, but they aren't necessary.  Plug those values into the firewall config files and you're good. 

I'm prepared to build my gateway and firewall on an old PII box running OpenBSD as OS.  This will be my 2nd stage.  But I expect to have all info available, not to be controlled by ISP. removing ISP's router for other use.

> 
Of course you will also need to set up a second NIC for the internal LAN side - pick a private IP range (most commonly 192.168.x.x) and you can either use fixed IPs in everything or set up a DHCP server for the LAN interface.  Some distros require explicitly enabling forwarding between the two NICs before any routing occurs, I don't know how BSD defaults.

My planning connection will be;-
ISP <-- Gateway <-- Server <-- Router (making use of ISP router) <-- Workstations

> 
I run Linux on mine though, usually Slackware since it's nice and light anyway and I'm so familiar with it.
I'm on my way building a new server running "slackware-11.0".  I have "slackware-11.0-install-dvd.iso" download and burnt on CD.  The new box is ready for installing OS.

Others noted with tks.

B.R.
satimis

---

### Post by RandomJoe on 2007-01-28
> **satimis said:**
> fixed IP - I have fixed IP/WAN for external
IP - What IP you are referring?
I meant that fixed external IP that you have.  You will have to tell the BSD/Linux box what its IP is for the "WAN/Inet" port.
> subnet mask - I have
gateway IP - I don't have ISP's gateway IP
DNS server - I can use ISP's DNS or OpenDNS
You'll need to have the gateway IP, otherwise your system won't know where to route packets with IPs outside your own subnet.  There are a few "tricks" I can think of that could figure out what the router uses, but they're a bit of a pain.  Easiest would be to ask the ISP.

On that thought, are you sure the router is actually configured for a fixed IP?  It is possible the ISP just recorded the router's MAC address and their system sends the same IP via DHCP whenever your router comes up.  If that's the case, you can just configure your new system to get an IP by DHCP and it will get all the necessary info automatically from the ISP.  You will have to set the network card's MAC address to the MAC of the router, though.

> My planning connection will be;-
ISP <-- Gateway <-- Server <-- Router (making use of ISP router) <-- Workstations
A few comments:

First, if you want your server directly accessible from the Internet, and you want the rest of your workstations behind the server, you could just forego the Gateway and put the firewall directly on the Server.  The Gateway is just adding another hop.

Alternatively, the way I have my home network set up is:

```

                                                                     |- Server
                                                                     |
ISP <-- Gateway <- Regular Ethernet switch  |- Desktop
                                                                     |
                                                                     |- Other workstations / AP / etc.

```
The Gateway forwards connect requests from the public IP to the server, everything "appears" from the outside to be on the public IP but the server is actually on a private IP.  And ONLY the ports I allow to be forwarded get to the server at all.

You _can_ use the ISP's router as a regular 'ol switch, if you just don't use the WAN port.  But there's no real need to use it as a router behind your gateway/server - it would be adding yet another layer of NAT that isn't needed.  (Your gateway or server - whichever is directly connected to the ISP - will need to be doing this as well, since you only get one IP.)

---

