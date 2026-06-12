---
title: "Webmin Setup DNS/DHCP/NAT/Port Forwarding/Domain"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by bumcheekcity on 2007-07-18
I'm pretty new with Ubuntu, but still, I've decided it best to setup a Server for my home. I want a system to manage my DNS/DHCP, and everything else in the title. I've installed Webmin on Ubuntu 7.04, and setup DHCP and DNS, by which I mean I set the computers on my network to automatically find everything, and they have network and Internet access. 

However, I need Port Forwarding, and I want a Domain, and I want a ******* of a Firewall, to lock down EVERYTHING, save the few ports I open and forward (my family are idiots). I also want to assign, in my server (not on the client computers), an internal IP address based on the MAC address of the PC (so my PC always gets the same internal IP, my brother's PC gets the same internal IP, etc.). I can do this in Windows Server 2003, and I really want a way of administrating this in Ubuntu. 

I'm not scared of the command line at all, but if there's a nice GUI way of doing this via Webmin, I'd prefer it.

---

### Post by bumcheekcity on 2007-07-19
Anyone at all able to help?

---

### Post by psyburn on 2007-07-19
I'm using a similar setup...
Ubuntu server 7.04 with DNS, DHCP, 
DHCP is IP assigned by MAC and a small extra DHCP pool
Firewall is locked down except for what few things I open.
I use kernel ip forwarding to get internal LAN to the outside and use Linux Firewall to do a NAT
My family doesn't need port forwarding but I do. 
However most things I would forward I end up usually ssh'ing in to the server box to do most of that.

I configure most of the server from Webmin.:guitar:

Ubuntu server or desktop (which did you install?)

EDIT:
BTW my setup (and also my advice) protects from incoming and does not restrict on outgoing.
I'm not terribly paranoid that way

---

### Post by bumcheekcity on 2007-07-19
I've got Ubuntu (well, Xubuntu), running with XFCE on a P3 1Ghz, 256MB RAM. It's not exactly steaming along, but for a server, it's OK. I'd really like to be cool enough to do this on a server-only environment, but one step at a time :D

How did you lock down IPs by MAC? I think I'll actually want no DHCP pool at all, that'll stop anyone that isnt authorised connecting, unless I key in their info. And, possibly the most important, how do you do the NAT and port forwarding? I assume NAT has been done automatically, because all my computers are accessing the internet without any problems (and without me manually assigning their IP/DNS/Gateway/etc. in the Network Settings of XP or similar screens in the Ubuntu clients. Is that a good assumption to make?

Could you give me either a way in webadmin to forward (for example) port 3389 (RDC) to my personal computer, if it's 192.168.0.2. The device connected to the internet is eth0, the device connected to the home network is eth1.

---

### Post by psyburn on 2007-07-19
Don't worry about your server specs mines a 800Mhz P3 384mb running Ubuntu Server that did all the same stuff and used to run Desktop.

I left a small DHCP pool in case something happens (new computer, adapter dies)
Also if they find out your address setup they can just set a unused static "In windows networking" and walk right around a need for your dhcp to give them one.
[hence a bad assumption especially if you use an open or WEP'd not WPA access point] 
They are separated however. xxx.xxx.xxx.05->19 for "known computers" while 25->29 for dhcp "unknown" computers.

in the dhcpd.conf file:
```
# Local
subnet 10.0.0.0 netmask 255.255.255.0 {
	authoritative;
	range 10.0.0.25 10.0.0.29;
        option domain-name-servers 10.0.0.1, 68.87.69.146, 68.87.85.98;
        option routers 10.0.0.1;
        default-lease-time 43200;
        max-lease-time 1209600;
=SNIP=
# Airlink+ MIMO PCI 
	host LucyLu {
		hardware ethernet 00:14:a5:d9:0d:74;
		fixed-address 10.0.0.14;
		}
```
also to get this to work you'll have to restart dhcp3-server from the command line

checking /var/log/auth.log or /var/log/syslog with bandwidth monitoring setup will show who's asking from where...

I've never port-forwarded through my server now that I think of it...
My bad...

---

### Post by psyburn on 2007-07-19
How did you  get NAT working or do you have a router device hooked up still, 'cause I don't think quite get your setup here, the way your writing it out.

Mine:
Cable modem
   |
eth1
===
Ubuntu Server:
ipv4.forwarding (or you can use ipmasq from apt-get)
iptables firewall
dns 
dhcp
===
eth0
  |
Switch --- Wireless AP
  |
Ubuntu 
Desktop



But what I'm afraid you might be using is:

ADSL/Cable Modem
   |
Router------ Your family
   |
Server

---

### Post by bumcheekcity on 2007-07-19
I'm on NTL so:

Cable Modem
|
eth0
===
Server
DNS
DHCP
NAT
... i think
===
eth1
|
Switch, my family, running XP and Linux. (There's no wireless AP)

I dont know exactly WHAT the Linux server is doing, but it's definately giving internet and Network to my family. There's also a Firewall turned on, ofc, but I dont know exactly how good it is, or exactly what it's blocking.

---

### Post by psyburn on 2007-07-19
You should install webmin immediately through the servers GUI.
Install webmin from the .deb package off [www.webmin.com](www.webmin.com)

What worries me is you say you don't know how its sharing/NAT 
To do mine, I tried to do the "simple" way of:
```
edit /etc/sysctl.conf
uncomment ipv4.forwarding
reboot

in webmin: [lots of clicks]
Networking --> Linux Firewall
reset firewall
block all on external interface eth1
setup firewall
add rule: [Accept incoming interface eth0 outgoing eth1]
add rule: [Accept incoming interface eth1 outgoing eth0 if connection states established,related]
create

show IPtable: (NAT)
POSTROUTING
add rule: [masquerade if outgoing interface eth1]
create
apply config
```
change ethX as you see the differences from yours and mine

really basic firewall/NAT that ***seems*** like no machine exists from the outside

EDIT: Poor grammar

---

### Post by bumcheekcity on 2007-07-19
Thanks for the advice, I'll try it when I get back home. When I do a ShieldsUp! test for all service ports, I see mainly blue. Is that good?

---

### Post by psyburn on 2007-07-19
I'm sure you want all green.
Especially if you wanted that locked down firewall you should get all green unless you opened a port, then you would get a red

---

### Post by bumcheekcity on 2007-07-19
Hmmm...

Well, I'll tell you what my "Linux Firewall" module looks like. Bearing in mind eth0 is my internet, and eth1 my Internal Network. 

> Incoming packets (INPUT)
	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 		
	Accept 	If input interface is lo 		
	Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED

Forwarded packets (FORWARD)
	Log packet 	If output interface is eth0 		
	Log packet 	If input interface is eth0
	
Outgoing packets (OUTPUT)
	Log packet 	If output interface is eth0

I've got bandwidth monitoring on, and it put all the 'Log Packet' things there. I've got the default action of INPUT and FORWARD set to Drop packets, but the default action of OUTPUT is to Accept. Any advice on securing it further, or port forwarding some ports or a range of ports? All green would be really nice :D

---

### Post by psyburn on 2007-07-19
I get all green with mine but like I said mine protects incoming and lets everything out.

The default action is a big deal. But from the looks of it I can assume


My Firewall:
[remember mine is eth0=LAN and eth1=internet ]
===========================
FILTER table (this is the one that comes up when you click "Linux Firewall")

INPUT
```
 	Accept | If input interface is lo		
	Accept | If protocol is TCP and TCP flags ACK (of ACK) are set 		
	Accept | If state of connection is ESTABLISHED 		
	Accept | If state of connection is RELATED 		
	Accept | If protocol is UDP and destination port is 1024:65535 and source port is 53 		
	Accept | If protocol is ICMP and ICMP type is echo-reply 		
	Accept | If protocol is ICMP and ICMP type is destination-unreachable 		
	Accept | If protocol is ICMP and ICMP type is source-quench 		
	Accept | If protocol is ICMP and ICMP type is time-exceeded 		
	Accept | If protocol is ICMP and ICMP type is parameter-problem
```
Default Action: Drop

FORWARD
```
 	Log packet | If output interface is eth1 		
	Log packet  | If input interface is eth1 		
	Accept | If input interface is eth0 and output interface is eth1 		
	Accept | If input interface is eth1 and output interface is eth0 and state of connection is ESTABLISHED,RELATED
```
Default Action: Drop

OUTPUT
```
 	Log packet | If output interface is eth1
```
Default Action: Accept
===========================
NAT table:

POSTROUTING
```
Masquerade | If output interface is eth1
```

---

### Post by psyburn on 2007-07-19
Another double post... :mad:

Modified from: [http://www.debian-administration.org/articles/73](http://www.debian-administration.org/articles/73)


For your wonderful Port Forward you'll need....
========================================
Show IPtable: (NAT)
PREROUTING
```
Destination NAT | If incoming is eth0 and destination port is 3389
```
[you'll specify  address 192.168.0.2 and port 3389 in their respective boxes when adding this rule]

Show IPtable: (FILTER)
INPUT
```
Accept | If incoming is eth0 and destination port is 3389
```

Then click "Apply Configuration" at the bottom and you should get that port forwarding you wanted.

---

### Post by bumcheekcity on 2007-07-19
OK, perhaps we're using slightly different versions of Webmin, because I dont have the option, it seems, for just enabling ports without specifiying TCP or UDP. Also, I can't select them both, which is REALLY annoying. Here's what I have now. 

> **Packet Filtering (FILTER)**

Incoming packets (INPUT)
	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 		
	Accept 	If input interface is lo 		
	Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED 		
	Accept 	If protocol is TCP and input interface is eth0 and destination port is 3389 		
	Accept 	If protocol is UDP and input interface is eth0 and destination port is 3389 
		
Forwarded packets (FORWARD)
	Log packet 	If output interface is eth0 		
	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 and output interface is eth0 		
	Accept 	If input interface is eth0 and output interface is eth1 and state of connection is ESTABLISHED,RELATED 		
		
Outgoing packets (OUTPUT)
	Log packet 	If output interface is eth0

> **Network Address Translation (NAT)**

Packets before routing (PREROUTING)
	Accept 	If input interface is eth1 		
	Accept 	If input interface is lo 		
	Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED 		
	Accept 	If protocol is TCP and destination is 192.168.0.2 and input interface is eth0 and source and destination ports are 3389 		
	Accept 	If protocol is UDP and destination is 192.168.0.2 and input interface is eth0 and source and destination ports are 3389 	
		
Outgoing packets (OUTPUT)
There are no rules defined for this chain.
		
Packets after routing (POSTROUTING)
	Masquerade 	If output interface is eth0

Defaults are:
Drop - FILTER: Input
Drop - FILTER: Forward
Accept - FILTER: Output
Accept - NAT: Prerouting
Accept - NAT: Output
Accept - NAT: Postrouting

So far (i'm still at work), I can't test if it's secure or not, but port 3389 isnt routing through to my home machine, using what I put there.

---

### Post by bumcheekcity on 2007-07-19
Oh great. I just pressed the 'Apply Configuration' button, and now the server is timing out. Well, I suppose that's secure. Any advice on what I just ****** up?

---

### Post by psyburn on 2007-07-19
Um, changing these default actions in while your away from (see also: can't reach it locally) the server isn't a good idea.
But have no fear it happens to the best of us...

If your using webmin from work you'll need:
```

Accept | If protocol is TCP and destination port is 10000
```

But its a little late for that now....

Once "Input default action: Drop" was added you cut yourself off since the webmin port wasn't opened.

You'll also need a bunch of those rules that I had in the input field for better connectivity.

It's easy enough to add them by hand.....when you get home.

EDIT: I'm using Webmin 1.35 and I've been using since 1.30

---

### Post by bumcheekcity on 2007-07-19
LOL! Ah, I'm such an idiot :D Ah well, it's not the end of the world. I break in 15 minuites. Out of interest, IS there a way of Adding both TCP AND UDP simultaneously? Because doing them one at a time is irritating lol.

Thanks for all your help, by the way, it's been fantasic :D

---

### Post by psyburn on 2007-07-19
Attached is a screencap of adding that DNAT in PREROUTING rule

EDIT: No I've not found a way to add both TCP and UDP in the same rule. 
I don't think it's possible with IPtables.
I usually use "clone rule" button
[click on the rule you want to copy, scroll to bottom and click clone rule, edit TCP to UDP and save rule]

EDIT2: The port next to the ip in the image says 80 but it needs to be 3389

---

### Post by bumcheekcity on 2007-07-19
OH, I see. Yeah, I was doing that completely wrong lol. Thankyou for that. Will let you know if it works in about 25 mins... Stupid work...

---

### Post by bumcheekcity on 2007-07-19
Right, I think I'm almost there. I'm getting perfect Green in ShieldsUp!, which is really good. Now I just need to forward ports 3380:3399 to 192.168.0.2 and I want a way of locking down my DHCP to MAC addresses. I include my current configuration below.

> **Packet Filtering (FILTER)**

Incoming packets (INPUT)
	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 		
	Accept 	If input interface is lo 		
	Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED 		
	Accept 	If protocol is TCP and input interface is eth0 and destination port is 3389 		
	Accept 	If protocol is UDP and input interface is eth0 and destination port is 3389 
		
Forwarded packets (FORWARD)
	Log packet 	If output interface is eth0 		
	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 and output interface is eth0 		
	Accept 	If input interface is eth0 and output interface is eth1 and state of connection is ESTABLISHED,RELATED 		
		
Outgoing packets (OUTPUT)
	Log packet 	If output interface is eth0

> **Network Address Translation (NAT)**

Packets before routing (PREROUTING)
 	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 		
	Accept 	If input interface is lo 		
	Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED 		
	Accept 	If protocol is TCP and destination port is 10000 		
	Accept 	If protocol is UDP and input interface is eth0 and destination port is 3380:3399 		
	Accept 	If protocol is TCP and input interface is eth0 and destination port is 3380:3399
		
Outgoing packets (OUTPUT)
There are no rules defined for this chain.
		
Packets after routing (POSTROUTING)
	Masquerade 	If output interface is eth0

Defaults are:
Drop - FILTER: Input
Drop - FILTER: Forward
Accept - FILTER: Output
Accept - NAT: Prerouting
Accept - NAT: Output
Accept - NAT: Postrouting

---

### Post by psyburn on 2007-07-19
the rule for webmin TCP port 10000 needs to be on the FILTER page->INPUT Chain not the NAT page.
accessing the server itself belongs on the FILTER page

also if you need a range of ports forwarded you'll need to open them as well on the FILTER page->INPUT Chain

As for the assigned IP Lock down you'll need to use the sample I gave earlier.

In webmin:
Servers --> DHCP Server
tell me if you have a 192.168.0.0 in the "Subnets and Shared Network" section

---

### Post by bumcheekcity on 2007-07-19
I've Removed the port 10000 rule from the NAT page, and I've added two chain rules to accept those Incoming on eth0, where protocol is TCP and port from 3380:3399 (and another identical one for UDP), but the ports arent forwarding. And, in the DHCP server, I do have the 192.168.0.0 in the Subnets and Shared Networks suggestion.

---

### Post by psyburn on 2007-07-19
```
Packet Filtering (FILTER)

Incoming packets (INPUT)
=SNIP=
Accept If protocol is TCP and input interface is eth0 and destination port is 3389
Accept If protocol is UDP and input interface is eth0 and destination port is 3389 
=SNIP=
```

Needs to read:
```
Packet Filtering (FILTER)

Incoming packets (INPUT)
=SNIP=
Accept If protocol is TCP and input interface is eth0 and destination port is 3380:3399
Accept If protocol is UDP and input interface is eth0 and destination port is 3380:3399 
=SNIP=
```

EDIT: Also for some rules like these port forwards DON'T put a adapter name. You can spend time later securing that more.

Make this happen and try again, then we'll focus on the DHCP

---

### Post by bumcheekcity on 2007-07-19
DHCP is working fine. I edited it in gedit and it worked perfectly, and I kept a few spare in a DHCP pool :D

I've made the edit. I'll post my current screen now. 

> **(FILTER)**

Incoming packets (INPUT)
	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 		
	Accept 	If input interface is lo 		
	Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED 		
	Accept 	If protocol is TCP and destination port is 10000 		
	Accept 	If protocol is UDP and input interface is eth0 and destination port is 3380:3399 		
	Accept 	If protocol is TCP and input interface is eth0 and destination port is 3380:3399
		
Forwarded packets (FORWARD)
	Log packet 	If output interface is eth0 		
	Log packet 	If input interface is eth0 		
	Accept 	If input interface is eth1 and output interface is eth0 		
	Accept 	If input interface is eth0 and output interface is eth1 and state of connection is ESTABLISHED,RELATED 		
		
Outgoing packets (OUTPUT)
	Log packet 	If output interface is eth0 
		
Chain Ports
	Accept 	If protocol is TCP and input interface is eth0 and destination port is 3380:3399 		
	Accept 	If protocol is UDP and input interface is eth0 and destination port is 3380:3399

**(NAT)**

Packets before routing (PREROUTING)
	Accept 	If input interface is eth1 		
	Accept 	If input interface is lo 		
	Accept 	If input interface is eth0 and state of connection is ESTABLISHED,RELATED 		
	Destination NAT 	If protocol is TCP and input interface is eth0 and destination port is 3380:3399 		
	Destination NAT 	If protocol is UDP and input interface is eth0 and destination port is 3380:3399 	
		
Outgoing packets (OUTPUT)
There are no rules defined for this chain.
		
Packets after routing (POSTROUTING)
	Masquerade 	If output interface is eth0

The defaults are still Drop, Drop, Accept, Accept, Accept, Accept as you go down the list.

---

### Post by psyburn on 2007-07-19
as far I can tell it should work
check the firewall on the internal machine and turn it off while you try remote access
you should NOT have to worry as you are properly firewalled now.
also make sure the ip is still the same on the internal machine.

domain is the only thing left I can help you with for now.

[www.dyndns.org](www.dyndns.org)
register for a domain
you will want to choose a less frequently used password when registering
I have no idea about the security of the client to dyndns for passwords to update.

then use this command in a shell on the server:
```
sudo apt-get install ddclient
```
follow the prompts for registry, domain-name, username, and password and you should be able to webmin home within a few hours 
(e-mail verification can take a bit oh 2 hours in my case)

EDIT: I'm tired and it shows

---

### Post by bumcheekcity on 2007-07-19
Ah, I won't worry about port forwarding, I'll leave that for another day. Thankyou for everything, it's been brilliant help :D

---

### Post by psyburn on 2007-07-19
You're welcome.

I generally use webmin and ssh for my server access.
Keeps me happy.

remember to check your logs and keep your server up-to-date.
Keep the rest of us safe by keeping yourself safe.

Cheers!:guitar:

---

### Post by bumcheekcity on 2007-07-28
I'm still really struggling to do the port forwarding in Webmin, and need help. Can anyone advise me of the most basic? Lets say I want to forward port 5000 from 192.168.0.1 (my Linux Server) to 192.168.0.6 (my PC). The internet comes through the Linux server on eth0, and the home network goes out through eth1.

---

### Post by bumcheekcity on 2007-07-28
bump

---

### Post by foging on 2007-10-31
Setting up port forwarding

On a network that uses NAT to hide internal systems from the Internet, outside hosts cannot connect directly those on the internal network. This is great for security, but can be annoying if there is some internal service that you do want to make available to the outside world. For example, your mail server system may not be the firewall host, which would normal make it inaccessible from the Internet. Fortunately, there is a solution to this problem - port forwarding.

This lets you re-direct all connections to some port on the firewall system to a different host and port on your internal network. For a mail server, all data received on port 25 might be send to the same port on the host that is actually being used to host user email. Of course, this would make it impossible for your firewall system to receive email itself.

To set up port forwarding, follow these steps :

   1. On the main page of the Linux Firewall module on the gateway system, select Network address translation from the list next to the Showing IPtable button before clicking it.
   2. In the Packets before routing section, click on Add rule to go to the rule creation form. The rule being added will redirect all external traffic received by the firewall to some internal address.
   3. Set the Action to take to Destination NAT.
   4. In the IPs and ports for DNAT field, select IP range and enter the address of the internal host into the adjacent text box, such as 192.168.1.10. In the Port range box, enter the port number on the internal host to which data should be sent, such as 25 for SMTP, 110 for POP3 or 80 for HTTP.
   5. Set the Network protocol to Equals and select TCP.
   6. In the Destination TCP or UDP port field, select Equals from the menu and enter the external port number for which forwarding should be done into the adjacent text field. Typically this will be the same as the port entered in step 4.
   7. Hit the Save button to create the rule and return to the main page, and then click the Apply Configuration button. 

The only problem with this method is that connections from inside your network to the firewall system will not be forwarded to the other host.

---

### Post by bumcheekcity on 2008-03-18
I have revisited this problem on Easter Holiday ack form UNi, and discovered that my problem was not in thePREROUTING section of the Firewall, but rather in the FORWARD section. Simply put, I had default action set to "Drop". Once I changed the default action to "Accept", my ports were forwarded instantly, after I refreshed the Firewall rules.

Please, though, don't change the default action for the INPUT section to "Accept". This will make your network insecure. The default action for this sould be set to "Drop". Ports will still forward correctly. Hopeyully, someone will find this information of assistance to them.

---

### Post by draggy on 2008-04-08
> **psyburn said:**
> I get all green with mine but like I said mine protects incoming and lets everything out.

The default action is a big deal. But from the looks of it I can assume


My Firewall:
[remember mine is eth0=LAN and eth1=internet ]
===========================
FILTER table (this is the one that comes up when you click "Linux Firewall")

INPUT
```
 	Accept | If input interface is lo		
	Accept | If protocol is TCP and TCP flags ACK (of ACK) are set 		
	Accept | If state of connection is ESTABLISHED 		
	Accept | If state of connection is RELATED 		
	Accept | If protocol is UDP and destination port is 1024:65535 and source port is 53 		
	Accept | If protocol is ICMP and ICMP type is echo-reply 		
	Accept | If protocol is ICMP and ICMP type is destination-unreachable 		
	Accept | If protocol is ICMP and ICMP type is source-quench 		
	Accept | If protocol is ICMP and ICMP type is time-exceeded 		
	Accept | If protocol is ICMP and ICMP type is parameter-problem
```
Default Action: Drop

FORWARD
```
 	Log packet | If output interface is eth1 		
	Log packet  | If input interface is eth1 		
	Accept | If input interface is eth0 and output interface is eth1 		
	Accept | If input interface is eth1 and output interface is eth0 and state of connection is ESTABLISHED,RELATED
```
Default Action: Drop

OUTPUT
```
 	Log packet | If output interface is eth1
```
Default Action: Accept
===========================
NAT table:

POSTROUTING
```
Masquerade | If output interface is eth1
```

I've followed your setup because I have the exact same. What I need to do is figure out how to get web access to my clients? The NAT doesn't seem to be working, and I've tried many many examples, including your's on my gutsy server. I've even tried forwarding port 80, but that doesn't help either. 

I guess my first question is, do I need to forward port 80 or do anything else to give net to the clients on the internal NIC?

---

