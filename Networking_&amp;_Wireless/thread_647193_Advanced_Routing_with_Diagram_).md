---
title: "Advanced Routing with Diagram :)"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by notaloafer on 2007-12-22
Attached is what my new network is going to look like.

**Here's my question:**
What do I need to get for the main router? I need to know 

_The main router must:_
1) Have a remote interface that I can manage remotely of course :)
2) Be able to handle as much traffic as the 10Mbps / 1Mbps connection can handle
3) Have some sort of DoS defense mechanism (however basic it is)
4) Be able to handle 5+ IP addresses and delegate them appropriately 
5) Be able to hand over full control of traffic to each of the 4 servers on the LAN

The most important part is being able to hand full control of the ports, etc. to the servers on the LAN (I guess technically it's not called a LAN anymore if you do it this way). I plan on leasing out a few of these dedicated servers and they need to pretty much have no interference from the main router at all; each server will have its own firewall where the end client can decide what traffic they allow/deny. What is the technical term for what I'm trying to do (I'm sort-of new to this kind of routing =P).

Another important part is the aspect that the sub-network needs to be as isolated as possible. I believe a Linksys WRT54G sub-router should be able to handle that part fine? I guess we can just allot 1 dedicated IP address to the router to run the sub-network?

I was looking into the Watchguard Fireboxes... those routers not only look cool but provide the features I'm looking for. Any ideas on what I'd need in their line of products (if you're familiar with them)?

Again, thank you guys so much for all the support you've given me! This community rocks the most by far! I know that there are a ton of questions in the above material I wrote, but if you have answers to any of them please post below.

Thanks!!!!!
-Eric

---

### Post by foolsh on 2007-12-22
I think* think you could bridge the connections,
look up "bridge-utils" see if that is what you're after

---

### Post by notaloafer on 2007-12-22
> **foolsh said:**
> I think* think you could bridge the connections,
look up "bridge-utils" see if that is what you're after

I'm mainly looking for suggestions on the type of router I need to purchase to satisfy the needs for the above network diagram (and also any other questions you can answer in the first post).

Are you referring to how I can setup the sub-network or something else?

Thanks
-Eric

---

### Post by PreviousN on 2007-12-22
I'm confused about your setup. When you say you have five static ips, does that mean you have like 5 cables from the modem to the router? I'm pretty sure that unless your doing some funky vlan stuff, one cable from a modem to one ethernet card = 1 ip address (without vlans). 

Either way, you do realize that you can make your own linux based router? If you live by a university, you can go to a "central store" there (basically where they recycle used computers) and buy computers on the cheap. For example, I live in california and went to my local university clearance house and got a 1Ghz computer with 512 MB of ram for 15 dollars. I had to buy a hard drive for it, but that was cheap and I use it as a network storage box anyways. ...Continuing...

Once you do that (buy a cheap box),  just buy some el cheapo ethernet cards and put em in the box. You could then run pfsense in a VM - what my friends do - (which, btw, pfsense is a freebsd, I think, distribution). This provides a web interface with seriuos easy to configure security (no messing with iptables). Or, you could install openwrt on your box and use ipkg to update. Or, you could use debian. I know this is a ubuntu forum, but I've heard some sketch things about ubuntu server. 

Well, so once you have all that set up, you can administer it remotly using ssh on a nonstandard port (ie: 1337) :-) or telnet :-(. And, if you have a web interface, you can block the outside world from accessing it, and if you need to see a webif when away, then use ssh to forward port 80 to tunnel your webif. Hows that sound?

---

### Post by notaloafer on 2007-12-22
> **PreviousN said:**
> I'm confused about your setup. When you say you have five static ips, does that mean you have like 5 cables from the modem to the router? I'm pretty sure that unless your doing some funky vlan stuff, one cable from a modem to one ethernet card = 1 ip address (without vlans). 

Either way, you do realize that you can make your own linux based router? If you live by a university, you can go to a "central store" there (basically where they recycle used computers) and buy computers on the cheap. For example, I live in california and went to my local university clearance house and got a 1Ghz computer with 512 MB of ram for 15 dollars. I had to buy a hard drive for it, but that was cheap and I use it as a network storage box anyways. ...Continuing...

Once you do that (buy a cheap box),  just buy some el cheapo ethernet cards and put em in the box. You could then run pfsense in a VM - what my friends do - (which, btw, pfsense is a freebsd, I think, distribution). This provides a web interface with seriuos easy to configure security (no messing with iptables). Or, you could install openwrt on your box and use ipkg to update. Or, you could use debian. I know this is a ubuntu forum, but I've heard some sketch things about ubuntu server. 

Well, so once you have all that set up, you can administer it remotly using ssh on a nonstandard port (ie: 1337) :-) or telnet :-(. And, if you have a web interface, you can block the outside world from accessing it, and if you need to see a webif when away, then use ssh to forward port 80 to tunnel your webif. Hows that sound?


All 5 ip addresses come in on one Comcast Cable line. The different servers are set up to "listen" on the different IP's and the traffic should work that way. The router I'm looking for is just going to control which servers can listen on what IP(s) so there are no conflict issues.

I'm aware that I can buy a cheapo computer and set it up as a router but that uses way too much electricity (the amount of electricity a older computer uses in one year setup as a 24/7 router would cost more than if I just bought a nice router to use). 

Thanks
-Eric

---

### Post by PreviousN on 2007-12-24
You may consider getting a openwrt compatible router then. I've personally got a wrt54g V.2 that I've installed openwrt on. And it sounds like you understand your stuff, so you should be able to just dive right in!

Make sure when buying a small router like the wrt (especially from linksys) that you take care in model numbers. I know that the wrt54g V 1-4 are compatable, but then once they were bought by cisco they cut back on the memory and used a propietary firmware. V5-8 or so of the wrt54g aren't very well supported. But you can still buy a wrt54gl which is a "linux version". 

You may also try a buffalo whr-54g-hp. These are pretty good. I've personally got a whr-54g that I've installed ddwrt on (I could install openwrt, but this needs to be accessible by my roomates, and I don't think they enjoy admining over ssh as much as I do...). 

Either ways, I think you may be doing something a little bit over my head, but those are my recommendations for a CHEAP, production/ready built router that consumes little power and can be administered over ssh (or a webif). Since it runs linux, you can do some cool stuff with the vlans and etc. 

Cheers!

---

### Post by burbankmarc on 2007-12-24
What you intend to do is pretty simple:

If you want to go with a linux box as your router, that's cool, it'll work great, and you can throw snort on it to do your intrusion detection stuff. All you'll need is 3 NICs in it.

1 NIC will be connected to your cable modem, another to a switch for your DMZ, and the last to your local network. 

Do ip masquerading on your local network, for all your NAT needs. Then your NIC connected to your DMZ will just do basic routing. 

Setup all your servers with the external addresses. 

This a basic overview of what you need to do. If you need a more indepth analysis feel free to ask.

---

### Post by trobbins on 2007-12-24
A WRT-54G with a modded firmeware should easily manage your network.   I was looking at Mini-ITX systems that use between 18 and 25 watts, but they are 300+ US dollars.  One of those systems could be a full UTM appliance though.  An alternative to a brand new mini-itx system would be using a Celeron 566mhz system.    The processor uses 11 watts.  Throw in a couple NICs and a HDD or CF adapter and you are set.

I don't trust the WRT54G's reliability.  Every person that I know has at one time in their life had to power cycle the router in order to restore connectivity.  I've locked mine up every week while using bittorrent.  I'm not sure how your scenario would work, but if I were you and my customers demanded 99.99% uptime, I would use an x86 system or a commercial UTM/firewall/router.

---

### Post by PreviousN on 2007-12-24
Personally, my wrt has very little downtime . But it is true...if your customers demand a lot of uptime, you shouldn't skimp on the router. 

Here's the uptime of my buffalo router :-) 

==========================================================
 
 ____  ___    __        ______ _____         ____  _  _ 
 | _ \| _ \   \ \      / /  _ \_   _| __   _|___ \| || | 
 || | || ||____\ \ /\ / /| |_) || |   \ \ / / __) | || |_ 
 ||_| ||_||_____\ V  V / |  _ < | |    \ V / / __/|__   _| 
 |___/|___/      \_/\_/  |_| \_\|_|     \_/ |_____|  |_| 
 
                       DD-WRT v24
                   [http://www.dd-wrt.com](http://www.dd-wrt.com)
 
==========================================================


BusyBox v1.4.2 (2007-10-10 01:13:37 CEST) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

~ # uptime
 20:41:09 up 23 days,  7:58, load average: 0.06, 0.06, 0.00

==========================================

Its only 23 days because I accidentally unplugged it 23 days ago. Before then I had about a month or so. Its pretty reliable.

---

### Post by jinx099 on 2007-12-25
I vote for pfsense as previously mentioned.  It is great software built on a rock solid OS (FreeBSD).  I run pfsense on hacked together parts and here is my uptime:
```
# uptime
10:44PM  up 168 days,  1:50, 2 users, load averages: 0.00, 0.00, 0.00
```
The last time I shut it down was just to put some gigE network cards in.  I highly recommend it.  If you don't want to run another PC full time, you can run pfsense on a little embedded system computer.  Check them out here:  [http://www.soekris.com/](http://www.soekris.com/)

pfsense list more pages here:  [http://www.pfsense.com/index.php?id=40](http://www.pfsense.com/index.php?id=40)

---

