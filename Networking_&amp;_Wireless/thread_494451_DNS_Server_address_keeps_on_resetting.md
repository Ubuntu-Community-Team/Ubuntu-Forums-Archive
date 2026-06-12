---
title: "DNS Server address keeps on resetting"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by ghettro on 2007-07-06
Hi,  I am running Feisty with a shared internet connection, When set to DHCP it automatically obtains all the settings; for some reason the DNS supplied by the router pretty much slows it down to a crawl and POP email doesnt work plus many other things.  I set the DNS to 203.2.75.2 which is an external server which makes it work perfectly.  However the bloody DNS keeps on resetting to default which is 192.168.0.1 which makes it nearly impossible to use.  Even after deleting that DNS and adding my own, it works perfectly until it refreshes itself, deletes my DNS server and reverts back to default.  It keeps on doing this every 5-10mins or so.

I have done a search on this and edited the DHclient.conf uncommented the prepend line and entered my own DNS.   This didnt change anything, it kept on resetting itself.
I then removed the "domain-name-servers" from the request line after that, which changed nothing either.  As I am typing now it has again reset itself.

any ideas??

note:  I am dualbooting XP, this had the exact same problem, except the DNS setting stayed put and I haven't had a problem with it since

---

### Post by bukwirm on 2007-07-06
In the router's configuration, there should be a place to set DNS server addresses - enter your DNS server addresses there.

By the way, what router do you have?

---

### Post by ghettro on 2007-07-10
OK, update.  Got everything working.  It was silly, just needed a reboot after uncommenting the prepend line and putting in my own DNS in that dhclient.conf file worked.

Somehow it'd be nice if I didnt have to revert to text editing, these things should just work.

---

### Post by archon256 on 2008-02-01
I realised that my router was resetting the DNS to the wrong 192.168.1.1 every 10 seconds and even if I wrote via Network Settings (KDE) or directly into resolv.conf to use an alternative good one (194.72.6.51) after 10 seconds it got overwritten again to the 192.168.1.1  I was getting desperate and furious. Windows machines kept the alternate DNS in IP configuration without problems. 
Then I found out (through a OpenSuse Live CD and YAST configuration) that to turn off the setting DNS via DHCP I had to change the resolv.conf instead of 

search -name-
nameserver 192.168.1.1

to 

domain site 
nameserver 192.168.1.1
nameserver 194.72.6.51

That helped, since then the DNS stays as it should and my internet is working 100%

---

