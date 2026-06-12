---
title: "Ports not opening despite router and firewall configurations."
date: 2014-06-30
forum: Networking &amp; Wireless
---

### Post by bar3m on 2014-06-30
I'm attempting to run a home hosted web application.

So far the project is done, and now i'm struggling for my web service to be online.

Access to the application is provided through two protocols : http for internet browsing (set at port 80 forwarded to another internal port running node.js, let's say port 8080 ( this part is already working fine ) and the web application itself, listening at an arbitrary port of my choice, i put 4444.

Config:
Router(192.168.0.1) port 80 & 4444 ----> Server (192.168.0.xxx)

External IP (eg.) 123.456.789.111

What i've done so far was:
- Forwarding ports 80 and 4444 to the web server's internal IP from the router's administration panel
- Adding iptables rule on my ubuntu 14.04 server to accept incoming connections on both port 80 and 4444 (i've double checked with iptables -L after rebooting the machine, the rule was correctly set up and it's appearing in the rule list) (i've temporarily disabled all the other rules and routings as well)

What comes up when running the portscan:

Scan on my server's internal ip address
> 
[FONT=Menlo]~ andrea$ nmap 192.168.0.xxx[/FONT][FONT=Menlo]
[/FONT]
[FONT=Menlo]Starting Nmap 6.46 ( [http://nmap.org](http://nmap.org) ) at 2014-06-30 11:23 CEST[/FONT]
[FONT=Menlo]Nmap scan report for 192.168.0.xxx[/FONT]
[FONT=Menlo]Host is up (0.0026s latency).[/FONT]
[FONT=Menlo]Not shown: 996 closed ports[/FONT]
[FONT=Menlo]PORT     STATE SERVICE[/FONT]
[FONT=Menlo]80/tcp   open  http[/FONT]
[FONT=Menlo]139/tcp  open  netbios-ssn[/FONT]
[FONT=Menlo]445/tcp  open  microsoft-ds[/FONT]
[FONT=Menlo]4444/tcp open  krb524[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Nmap done: 1 IP address (1 host up) scanned in 1.41 seconds[/FONT]

Scan on my public ip address done from within my ISP subnet:
> 
[FONT=Menlo]~ andrea$ nmap 123.456.789.111[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Starting Nmap 6.46 ( [http://nmap.org](http://nmap.org) ) at 2014-06-30 11:25 CEST[/FONT]
[FONT=Menlo]Nmap scan report for [/FONT][FONT=Menlo]123.456.789.111[/FONT]
[FONT=Menlo]Host is up (0.0076s latency).[/FONT]
[FONT=Menlo]Not shown: 996 closed ports[/FONT]
[FONT=Menlo]PORT     STATE    SERVICE[/FONT]
[FONT=Menlo]53/tcp   open     domain[/FONT]
[FONT=Menlo]80/tcp   open     http[/FONT]
[FONT=Menlo]3333/tcp filtered dec-notes[/FONT]
[FONT=Menlo]4444/tcp open     krb524[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]Nmap done: 1 IP address (1 host up) scanned in 1.43 seconds[/FONT]


_**If i try to run the portscan from outside my provider's ISP subnet, the portscan returns all ports closed except port 80.**_

I called my ISP and they keep swearing they don't block any ports and it must be a router's problem
I called my router's productor but I was already doing the port forwarding correctly so they couldn't be of any help.

I'm about to buy a VPS and forget about this in some hours, but i'm trying to post this so that maybe someone with a better understanding may help.

What is bugging me here is the fact a customer is not getting what he has paid for: it's like buying a machine and discovering it can't steer left after some miles. :mad:

---

### Post by TheFu on 2014-06-30
It doesn't look like you are doing anything wrong to me, but some routers will block access to the public IP (WAN interface) as anti-spoofing security.  Can you turn off the SPI on the router?  The specific router firmware could be helpful too - any chance you could replace it with dd-wrt, openwrt, or tomato?  I've found that netgear firmwares ... er ... suck if you aren't a grandma consumer.

How about trying different ports and doing the setup again?  Does your router firmware allow port translations? Start with that first.

---

### Post by gordintoronto on 2014-06-30
There is still the chance that your ISP is lying through his teeth, and they block web servers. Possibly the person you talked to doesn't understand that it means blocking port 80.

---

### Post by bar3m on 2014-07-11
At the end I turned around the problem by buying a VPS.

BTW for info:
I double checked the router configuration by connecting it from a different location, different ISP and I could indeed ping my webapp. I'm pretty sure either my ISP Infostrada or our monopolist network cables owner Telecom is blocking ports. 

(Keep in mind Infostrada recently issued Telecom for allegedly providing better network performance to his own users than the others from concurrent ISPs)

---

