---
title: "[SOLVED] Firefox/Epiphany/Lynx not loading certain websites"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by prshah on 2008-03-08
Hello,

I am having some internet problems in Ubuntu.

My machine is connected via eth0 to my wireless adsl router.

The internet works fine, eg when downloading with Deluge, or with streaming audio, pidgin instant messenger, etc.

But when I am browsing, certain sites do not open. All firefox does is display a "Loading..." in the tab and the loading pinwheel.

I have checked my ISP's DNS servers, my routers DNS settings and even setup OpenDNS on router as well as in the local machine.

There are no specific sites that refuse to open; it varies randomly. Any number of refreshes (sometimes, when frustrated, I do 10-15 in a matter of seconds; worked in Windows, doesn't here) do not help. and it's definitely not an HTTPS issue, since my banking and other sites work fine.

My usual sites such as ubuntuforums.org, google etc open fine. In fact, Google opens amazingly fast and operates very smoothly. 

One point: don't laugh: the [www.microsoft.com](www.microsoft.com) website NEVER opens. A continuous "Loading..." pinwheel is displayed for a long time, followed by a "Problem loading page" and "The connection was reset."

"nslookup www.microsoft.com" returns this:

```
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
www.microsoft.com       canonical name = toggle.www.ms.akadns.net.
toggle.www.ms.akadns.net        canonical name = g.www.ms.akadns.net.
g.www.ms.akadns.net     canonical name = lb1.www.ms.akadns.net.
Name:   lb1.www.ms.akadns.net
Address: 207.46.19.190
Name:   lb1.www.ms.akadns.net
Address: 207.46.19.254
Name:   lb1.www.ms.akadns.net
Address: 207.46.192.254
Name:   lb1.www.ms.akadns.net
Address: 207.46.193.254

```

Ping to [www.microsoft.com](www.microsoft.com) fails to return anything, all other sites ping fine; maybe MS has disabled ping replies?

I have the following messages in my "/var/log/messages"... do they have any relevancy here?

```
dhcdbd: dhco_parse_option_settings: bad option setting: old_server_name =  
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

```

The funny thing is the "RedHat" messages, though I have only Ubuntu on the computer.

Cheers,
PRShah

EDIT: for your info: ipv6 already disabled using blacklist and disabled in firefox as well

---

### Post by ssj3strife on 2008-03-08
I noticed you mentioned you were using Deluge. If you start having trouble with a site, make sure Deluge is closed down. Some pieces of software (Deluge included, I think, and PeerGuardian is another) block communication with certain IPs and IP ranges that have been associated with various nefarious organizations. It's possible that the sites you have trouble with fall into these ranges, and it would be no surprise to me if MS managed to land themselves on a blacklist as well.

Long story short, close every program you can and see if the problem persists?

---

### Post by prshah on 2008-03-08
Yes, been there, done that. Should have mentioned it. Thanks for the effort and would appreciate any suggestions.

Cheers,
PRShah

---

### Post by unutbu on 2008-03-08
Regarding the dhcdbd errors in /var/log/messages:
According to man, dhcdbd returns the dhcp configuration. Since you seem to have a connection with your router, I doubt dhcdbd has anything to do with your problem.

Regarding microsoft:
My nslookup on [www.microsoft.com](www.microsoft.com) looks just like yours too.
Pinging [www.microsoft.com](www.microsoft.com) fails for me too. I suspect MS refuses to reply to pings.
So... I doubt that's your problem either.

If you point your browser at your router, can you tell your router to do a nslookup, ping and traceroute? Next time a site fails to load in firefox, perhaps try those tests. If the router fails to produce results, then you can conclude the problem isn't in your machine.

If your router succeeds with nslookup, ping and traceroute, then try running the same commands on your computer. Since you say the problem happens randomly,
also try the same three programs on the site at a time when their sites are loading in
firefox. Post all the results here. Maybe someone will get an idea.

---

### Post by ssj3strife on 2008-03-08
When you start to have trouble with a certain site, try visiting it by IP instead of domain name. (like [http://123.12.21.31](http://123.12.21.31)) Whether or not the site loads via IP would help narrow down where the problem might be.

---

### Post by prshah on 2008-03-08
> **prshah said:**
> 

One point: don't laugh: the [www.microsoft.com](www.microsoft.com) website NEVER opens. A continuous "Loading..." pinwheel is displayed for a long time, followed by a "Problem loading page" and "The connection was reset."

Ping to [www.microsoft.com](www.microsoft.com) fails to return anything, all other sites ping fine; maybe MS has disabled ping replies?



> **unutbu said:**
> 

Regarding microsoft:
My nslookup on [www.microsoft.com](www.microsoft.com) looks just like yours too.
Pinging [www.microsoft.com](www.microsoft.com) fails for me too. I suspect MS refuses to reply to pings.
So... I doubt that's your problem either.


And yet another MS would-be-visitor faces the same issue: 
[http://ubuntuforums.org/showthread.php?t=718848](http://ubuntuforums.org/showthread.php?t=718848)

I think it's an epidemic!

However, rather than Ubuntu blocking MS (as posted in the reference above), I think it's the other way around!

Anybody around here able to browse the MS website in Ubuntu?

Cheers,
PRShah

---

### Post by ssj3strife on 2008-03-10
MS' website loads fine for me. The only other advice I can offer is to call your ISP and see if they can offer any help - but I assume you have done that already. Beyond that, I don't know... maybe you could try plugging a different machine into the network interface you're using and see if it has the same troubles.

---

### Post by prshah on 2008-03-11
OK heres some more information:

Yahoo Mail doesn't open up at all; umpteen refreshes, browser changes et al;

when I give command 

```
"tracepath mail.yahoo.com" 
```I get:

> 
Wed Mar 12 01:23:14 ~:$ tracepath mail.yahoo.com
 1:  192.168.1.51 (192.168.1.51)                            0.191ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm  2   0.676ms 
 2:  59.92.80.1 (59.92.80.1)                              asymm  3  35.245ms 
 3:  no reply
 4:  no reply
 5:  125.17.21.29 (125.17.21.29)                          asymm  4  33.210ms 
 6:  125.21.167.74 (125.21.167.74)                         34.995ms 
 7:  p4-1-0-1.r03.lsanca03.us.bb.gin.ntt.net (204.1.253.65) 253.453ms 
 8:  xe-3-3-0.r20.lsanca03.us.bb.gin.ntt.net (129.250.2.141) asymm  7 257.395ms 
 9:  as-0.r21.snjsca04.us.bb.gin.ntt.net (129.250.4.96)   asymm  8 263.067ms 
10:  ae-0.r20.plalca01.us.bb.gin.ntt.net (129.250.4.118)  263.347ms 
11:  208.50.13.97 (208.50.13.97)                          asymm 12 311.611ms 
12:  no reply
13:  64.215.195.6 (64.215.195.6)                          312.175ms 
14:  ge-3-0-0-p261.msr1.scd.yahoo.com (216.115.106.187)   asymm 10 297.926ms 
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500 


Can anyone else here compare with their results?

Any ideas on the "no reply" lines?

Cheers,
PRShah

---

### Post by ssj3strife on 2008-03-12
I'd guess that's not indicitave of a problem. Here's mine:

> ben@ben-laptop:~$ tracepath mail.yahoo.com
 1:  ben-laptop.local (130.101.169.7)                       0.208ms pmtu 1500
 1:  130.101.160.1 (130.101.160.1)                          3.844ms 
 2:  130.101.26.150 (130.101.26.150)                        6.810ms 
 3:  akrnq-r3-ge-0-0-0s511.bb.oar.net (192.148.242.113)   asymm  4   3.480ms 
 4:  akrnq-r3-lt-0-1-0s12.bb.oar.net (199.18.245.33)      asymm  5   4.831ms 
 5:  akrnq-r0-ge7-2s505.core.oar.net (199.18.154.65)        3.166ms 
 6:  clevs-r0-po0-0.core.oar.net (199.18.145.10)            5.748ms 
 7:  clevs-r2-ge-3-0-5s923.bb.oar.net (199.18.156.254)    asymm  8   5.956ms 
 8:  199.18.156.246 (199.18.156.246)                      asymm  9  15.911ms 
 9:  so-0-2-0.0.rtr.chic.net.internet2.edu (64.57.28.12)   30.670ms 
10:  64.57.29.18 (64.57.29.18)                            asymm 11  30.126ms 
11:  vl141.bas2.dal.yahoo.com (216.115.96.37)             asymm 12  56.436ms 
12:  ge-0-0-6.pat2.dce.yahoo.com (216.115.102.117)        asymm 13  56.439ms 
13:  ge-2-1-0-p171.msr2.re1.yahoo.com (216.115.108.31)    asymm 14  56.758ms 
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1500
     Resume: pmtu 1500

---

### Post by prshah on 2008-03-12
> **ssj3strife said:**
> I'd guess that's not indicitave of a problem. Here's mine:

You're right; but your log has revealed a new thing; my ISP is probably ripping me off; just compare our step by step timings... mine are WAAAAAAYYYYY off!

Thanks for the trouble anyway... guess I will just give up.. 

Cheers,
PRShah

---

### Post by ssj3strife on 2008-03-12
Wow, you're right, I didn't even look at that. It'd be interesting to do a tracepath of a site that does load vs. a site that doesn't and compare those timings? Not that that would help much... I'm pretty sure there's nothing you can do on your end to remedy your situation.

---

### Post by prshah on 2008-03-14
> **prshah said:**
> Hello,

I am having some internet problems in Ubuntu.

My machine is connected via eth0 to my wireless adsl router.

The internet works fine, eg when downloading with Deluge, or with streaming audio, pidgin instant messenger, etc.

But when I am browsing, certain sites do not open. All firefox does is display a "Loading..." in the tab and the loading pinwheel.

I have checked my ISP's DNS servers, my routers DNS settings and even setup OpenDNS on router as well as in the local machine.

There are no specific sites that refuse to open; it varies randomly. Any number of refreshes (sometimes, when frustrated, I do 10-15 in a matter of seconds; worked in Windows, doesn't here) do not help. and it's definitely not an HTTPS issue, since my banking and other sites work fine.

My usual sites such as ubuntuforums.org, google etc open fine. In fact, Google opens amazingly fast and operates very smoothly. 

One point: don't laugh: the [www.microsoft.com](www.microsoft.com) website NEVER opens. A continuous "Loading..." pinwheel is displayed for a long time, followed by a "Problem loading page" and "The connection was reset."

```
dhcdbd: dhco_parse_option_settings: bad option setting: old_server_name =  
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

```

EDIT: for your info: ipv6 already disabled using blacklist and disabled in firefox as well

SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED SOLVED

All thanks to a chance link at [http://ubuntuforums.org/archive/index.php/t-619531.html](http://ubuntuforums.org/archive/index.php/t-619531.html) when looking for something else!

Quick summary: My router's MTU option was set to 1500, apparently thats not good, should be 1492. Made the change, restarted the router and BLAST!! My Internet is on fire, and all those doubts about dumping Windoze just VANISHED!

mail.yahoo.com opens like lightning, microsoft.com begs me to download and use Slivrlight technology etc etc.

I'm so excited that I can barely type straight!

I hope this is helpful to millions of others in the same situation!!

---

### Post by ssj3strife on 2008-03-15
Wow... ok! Well I'm glad to hear you got it sorted out! I know the basics of networking, but fixes like those still fall into the "black magic" category for me. 

At any rate, thanks for posting the fix! (And making me look like a dummy, for saying that I thought there was nothing you could do about it...) ;)

Seriously, glad to hear it's working for you now. :)

---

