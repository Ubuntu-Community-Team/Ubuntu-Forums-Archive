---
title: "Problems using DNS in multiple distributions"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by Verbatim9 on 2006-11-14
[edit]For anyone who finds this thread in a search: I did eventually solve my problems, what I needed to do was turn off IPv6 both system-wide (gives a general speed-up to everything internet related), and in Firefox (go to about:config, filter for ipv6, and double click the entry to set "network.dns.disableIPv6" to "true").[/edit]

I've been trying to get several different versions of Linux installed on a new computer, but all of them have had horrible problems with internet connectivity...the card itself seems to be configured correctly, DHCP finds the gateway and adds the nameservers correctly...and yet, names never get translated into addresses.

For example, if I type "www.battle.net" into my Firefox window, Firefox times out waiting for a response...but if I type "216.148.223.71" instead, the page loads almost instantly. Any ideas how that could be the case?


Here is my full hardware list, in case anyone recognizes something that could be causing incompatibility with both Ubuntu i386 Dapper and Edgy (tried both, same problem exists in both, as well as in KnoppMyth R5D1):

[Asus M2NPV-VM CSM](http://www.asus.com/products.aspx?l1=3&l2=101&l3=296&model=1138&modelmenu=1) motherboard (w/ integrated everything, GeForce 6130/Nforce 430 chipset)
AMD Athlon X2 (dual-core) 4200+ processor (65W version)
1GB Mushkin 800 MHz DDR2 RAM
NEC DVD-RW drive
2x 512GB SATA HD (Western Digital "Raid Edition")
Logitech wireless keyboard and mouse

I know others have gotten this board to work well, so I'm wondering if it could be an issue with using a dual-core CPU...or what else it could be that makes Ubuntu able to talk to any IP on the internet, and able to find my nameserver, but unable to reliably communicate with the nameserver.

---

### Post by bmillsap on 2006-11-14
If you run "nslookup www.battle.net" in a terminal window, what's the output like?  What nameserver does it use, and does it get the IP address for battle.net?

---

### Post by Verbatim9 on 2006-11-14
nslookup seems to work fine...
> $ nslookup [www.battle.net](www.battle.net)
Server: 192.168.0.1 (=my local gateway)
Address: 192.161.0.1#53

Non-authoritative answer:
[www.battle.net](www.battle.net)  cannonical name = battle.net
Name:    battle.net
Address: 216.148.223.71

---

### Post by bmillsap on 2006-11-14
Hmmm...well, I have no good ideas right offhand of what could be causing this.  I guess you can check that there aren't any proxy settings in Firefox, but if there were, that should be breaking access by IP also.  Out of curiosity, if you ping something by name, does it work?

---

### Post by Verbatim9 on 2006-11-15
Yep, pinging by name works just fine, too, 47.6-48.5 ms to ping [www.google.com...wish](www.google.com...wish) I could get a ping like that in Diablo II.

There are proxy settings in Firefox, but I don't use a proxy with my ISP...and it's set correctly to connect "directly" to the internet.

..it seems to be exactly the same problem as in [this thread](http://www.ubuntuforums.org/showthread.php?t=299757), but we have almost exactly opposite hardware (the laptop appears to be 100% Intel for the processor (which is single-core) and integrated video, and probably for the chipset, while mine is AMD/Nvidia), so I'm not at all sure what that says about the problem...you'd think it would have to be software or ISP related at that point.

It apparently only affects some programs...I installed Konqueror using aptitude, and it works just fine. There's also a related topic [here](http://www.ubuntuforums.org/showthread.php?t=288286), which I believe is someone else experiencing exactly this issue. Older versions of Dapper were apparently not affected, but the Firefox 1.5 included with the current version of Dapper is just as messed up as Firefox 2.0 in Edgy. 

Apparently some have found relief by installing Firefox 2.0 from the web, which suggests it could be a problem with how some of the binaries are being compiled for Ubuntu.

I'm a relative Linux noob, so do regard my theories with the appropriate level of cynicism, any suggestions as to what it might be that is going on, or how to fix it would be welcome.

---

