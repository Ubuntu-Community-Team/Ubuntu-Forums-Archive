---
title: "Networking keeping me from leaving the evil empire!"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by jeep_jeremy on 2005-11-08
I'm trying to switch my family to Open Source.  So I buy a laptop for the wife, install Ubuntu 5.10 while I'm at my office, configure wireless, everything works great.

Then I get home and hook up to the old Qwest DSL with the Actiontec 701 router.  I associate, get an ip address, I can even use the router admin page.  Thats it though.  I try browsing to any other site and it won't do it, or some times it will do it extremely slow.  Same for all other Internet apps.

What kind of problem would be keeping me from browsing through the router when the 4 other computers in my house (all windoze) can when it works on my office wireless LAN.

Help...

---

### Post by jeep_jeremy on 2005-11-08
P.S.  Same thing happens when I plug in to the wired interface

---

### Post by az on 2005-11-08
Does it connect with dhcp and did you mess around with the dns settings?

---

### Post by jeep_jeremy on 2005-11-08
It does connect with DHCP.  Haven't tried messing with DNS yet.  What would you suggest?  I didn't see any option on the router...

---

### Post by mips on 2005-11-09
Try configuring the DNS servers manually in your network settings instead of relying on the router to do it.
Go  System->Administration->Networking->DNS  and add your DNS servers manually.

Alternatively you might want to disable IPv6, **Option 1** in the thread below;
[http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by AkaWaka on 2005-11-09
I have exactly the same problem with my ubuntu install, while knoppix works without any issues.  I have manually added my dns servers as mentioned without any effect.

An interesting note, I can ping hosts outside my network, by name, without any problems, and, using firefox, I can browse a few web sites.  For the most part though, I am only able to access a handfull of systems outside my LAN.  Additionally, I am unable to add new packages to my box using the APT system.  I get numerous timeout errors, again, except for a handfull of hosts.

Another interesing similarity, I am using a Qwest DSL with an Actiontec router as well.

I haven't tried to disable IPV6 yet, so I will give that a whirl and see what happens.

---

### Post by jeep_jeremy on 2005-11-09
AkaWaka, sounds like we have the exact same problem.  I've tried the dns trick already, no dice.  I also can ping everything just fine.  Just can't do anything usefull (Firefox, gaim).

---

### Post by jeep_jeremy on 2005-11-09
> **mips]
Alternatively you might want to disable IPv6, **Option 1** in the thread below said:**
> http://ubuntuforums.org/showthread.php?t=78337[/url]

This did it.  Thanks for your help all!  The open source community proves its worth once again.

---

### Post by jeep_jeremy on 2005-11-09
Ok, so maybe I got too excited.  Everything else seems to be working, but gaim won't connect to anything.  Again, this worked at my office yesterday.

ipv6 is disabled now, could that have screwed up something for gaim?

---

### Post by mips on 2005-11-09
I dont htink so, if gaim is the only app not working then it must be something else i reckon but i could be wrong.

---

### Post by AkaWaka on 2005-11-09
[QUOTE=jeep_jeremy]Ok, so maybe I got too excited.  Everything else seems to be working, but gaim won't connect to anything.  Again, this worked at my office yesterday.

ipv6 is disabled now, could that have screwed up something for gaim?[/QUOTE]

I've got the same exact problem... removing the support for IPV6 helped almost everything, although I also needed to remove the acpi support on the grub loader boot line (acpi=off).  Since this is a laptop, I don't really like that, but at least I can connect the web.  Also, Synaptic works most of the time.  I still get timeout errors when I add items to my repositories.  

I'm certain that I had this same issue on another machine (desktop, not laptop) using the liveCD.  Could this be an issue with the Qwest DSL or Actiontec (GT701) router?

---

### Post by mips on 2005-11-10
[QUOTE=AkaWaka]I'm certain that I had this same issue on another machine (desktop, not laptop) using the liveCD.  Could this be an issue with the Qwest DSL or Actiontec (GT701) router?[/QUOTE]

This is a possibility. Some applications use certain TCP/UDP ports. I have seen instances where guys have had to enable port forwarding to make certain P2P applications faster for example.

---

### Post by jeep_jeremy on 2005-11-10
I have exorcised the demons on Gaim.  I just couldn't let this one beat me!

I was looking through the NAT table and for the port numbers on yahoo and msn messenger it had a destination ip of 1.0.0.0.  Some googling around hinted that 1.0.0.0 was an auto proxy configuration.

Here's my guess.  Auto proxy configuration was jacking up the crappy qwest router.  Once I turned it off on those messaging services and rebooted the router, viola!  No more problems.

So in closing, if you have a qwest actiontec router please disable ipv6 and auto proxy settings discovery.  Evidently the linux on the actiontec router doesn't "just work".

---

### Post by AkaWaka on 2005-11-10
[QUOTE=jeep_jeremy]Here's my guess.  Auto proxy configuration was jacking up the crappy qwest router.  Once I turned it off on those messaging services and rebooted the router, viola!  No more problems.[/QUOTE]

Excellent - maybe I'm a little slow, but where did you disable the "Auto Proxy configuration"?  Is that somewhere in the router? or GAIM settings?

---

### Post by mips on 2005-11-11
AkaWaka,
> 
Excellent - maybe I'm a little slow, but where did you disable the "Auto Proxy configuration"? Is that somewhere in the router? or GAIM settings?

From his post I would say it is in the router config:
> Here's my guess. Auto proxy configuration was jacking up the crappy qwest router. Once I turned it off on those messaging services and rebooted the router, viola! No more problems.

---

