---
title: "[SOLVED] Painfully slow internet whilst behind router in Hardy Heron (yes, I've done"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by phucough on 2008-07-16
Hi there,

Got a brand spanking new laptop so decided to install Hardy Heron on it (I've previously used Dapper Drake until my old PC killed itself a couple of years back).

Not got a wireless router so plugged it into the internet using an ethernet cable connected to a router.

Internet speed was about a quarter of that of dial up (56Kbps) when it should be 2Mbps.

I tried the ipv6 and OpenDNS advice given repeatedly on this site, but no joy.

I connected the laptop straight into the cable from the modem, and it was well fast again. So, the router's to blame.

So how can I get my laptop to bypass the router?

It's a LinkSys router. On other computers in my home I can access the router by typing 192.168.0.1 in my browser, however on the laptop when the router set up page finally appears, the top bar with all the links to the menus doesn't.

I don't know much about the ins and outs of networks so any help is gratefully appreciated.

---

### Post by alfalfa31 on 2008-07-16
I don't know how to solve your problem with the information given, but I do love your handle...

---

### Post by phucough on 2008-07-16
> **alfalfa31 said:**
> I don't know how to solve your problem with the information given, but I do love your handle...

Cheers, though it is a bit inappropriate for a forum where I ask for help! I can also lay claim to having created the term back in 2004 on the bianca forums - it has since been appropriated by a number of people. Why I'm proud of this fact, I don't know! :-k

---

### Post by alfalfa31 on 2008-07-16
> **phucough said:**
> Cheers, though it is a bit inappropriate for a forum where I ask for help! I can also lay claim to having created the term back in 2004 on the bianca forums - it has since been appropriated by a number of people. Why I'm proud of this fact, I don't know! :-k

We can only take pride in our creativity.  I'd be proud to have coined it as well...

"Inappropriate" is in the eye of the beholder.  I say, screw 'em if they can't appreciate humor...

---

### Post by phucough on 2008-07-17
Cheers alfalfa31!

To anyone who can help, here's some more info regarding the problem:

I tried OpenDNS and the ipv6 thing again and that didn't work.

I entered the router's setup through another computer and tried disabling the firewall and setting the laptop as a DMZ. They didn't work either.

I didn't have this trouble when I was using Dapper Drake.

Any suggestions?

---

### Post by ModelM on 2008-07-17
Read my response at the bottom of this short thread. Assuming the problem is with DNS, I think it may help you, also...

[http://ubuntuforums.org/showthread.php?t=860758](http://ubuntuforums.org/showthread.php?t=860758)

---

### Post by phucough on 2008-07-17
> **ModelM said:**
> Read my response at the bottom of this short thread. Assuming the problem is with DNS, I think it may help you, also...

[http://ubuntuforums.org/showthread.php?t=860758](http://ubuntuforums.org/showthread.php?t=860758)

Cheers for the response. I already tried that using a different method (using the GUI and adding the DNS to the list on the DNS tab) but I gave it a shot using this way... still no joy.

It would appear to be something to do with the router because it works fine plugged straight into the modem, although looking through all the router config options I cannot see what would fix it.

---

### Post by ModelM on 2008-07-17
If these solutions have not helped, the problem might not be DNS at all.

In a terminal, type:

ifconfig

and check the number of errors, overruns, and collisions on the interface (probably eth0). Values greater than zero for any of these might provide a clue...

---

### Post by phucough on 2008-07-17
Cheers, here's the results for eth0 from ifconfig (there's also lo but I don't know what that is):

```
eth0 Link encap:Ethernet HWaddr 00:1f:29:8b:91:0b
   inet addr:192.168.0.4 Bcast:192.168.0.255 Mask:255.255.255.0
   UP BROADCAST RUNNING MULTICAST MTU:1492 Metric:1
   RX packets:17 errors:8 dropped:0 overruns:0 frame:4
   TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:1000
   RX bytes:3768 (3.6 KB)  TX bytes:8288 (8.0 KB)
   Base address:0x4020 Memory: e4600000-e4620000
```

I plugged the cable in, rebooted it, and went into ifconfig without trying the internet... and there's 8 errors for RX packets.

---

### Post by ModelM on 2008-07-17
The error rate shown here is about 50% (8 errors in 17 packets), that's very high. Let it run for a bit then recheck it to see if the percentage is still so high. This could be a very good clue.

---

### Post by NEUR0M4NCER on 2008-07-17
Hi - sorry to butt in here, but it's the first clue i'va had in diagnosing my wireless connection problems. After running ifconfig, I get this:```
neur0m4ncer@box:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99875 (97.5 KB)  TX bytes:99875 (97.5 KB)

ra0       Link encap:Ethernet  HWaddr 00:11:50:8e:c5:5a  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe8e:c55a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66577 errors:1441 dropped:1441 overruns:0 carrier:0
          collisions:42249 txqueuelen:1000 
          RX bytes:49169075 (46.8 MB)  TX bytes:11514841 (10.9 MB)
          Interrupt:22 Base address:0x8000
``` Check out those errors! Is that actual evidence of my intermittent wireless connection? And if so, what do I do to correct it?

---

### Post by phucough on 2008-07-17
I've got the cable plugged in to my other PC now and I need to use the internet to help me blag a job interview tomorrow (I have to pretend to be an Access wizard and I can use it well but not to the level specified :)) but when I go to bed I'll plug the laptop in and leave it running overnight. I'll try to update the repositories and download Flash (a 2.9Mb file of which took nearly two hours to get halfway the other night), that should keep it busy...

Cheers for your help.

---

### Post by ModelM on 2008-07-17
NEUR0M4NCER:

Yes there are a lot of errors and also a huge number of collisions. I'm far from a wireless expert, but the first thing I'd try in your case is changing the channel your wireless router/access point uses.

---

### Post by phucough on 2008-07-18
Well, I left it running overnight and got this:

```
eth0 Link encap:Ethernet HWaddr 00:1f:29:8b:91:0b
   UP BROADCAST RUNNING MULTICAST MTU:1492 Metric:1
   RX packets:1239 errors:420 dropped:0 overruns:0 frame:239
   TX packets:1492 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:1000
   RX bytes:80356 (78.4 KB)  TX bytes:99919 (97.5 KB)
   Base address:0x4020 Memory: e4600000-e4620000

eth0:avahi  Link encap:Ethernet HWaddr 00:1f:29:8b:91:0b
   inet addr:169.254.4.142 Bcast:169.254.255.255 Mask:255.255.0.0
   UP BROADCAST RUNNING MULTICAST MTU:1492 Metric:1
   Base address:0x4020 Memory: e4600000-e4620000
```

This time it didn't even run slowly, just failed completely. What's all this avahi business and where did the weird inet addr come from? But also, loads of errors.

---

### Post by phucough on 2008-07-18
> **phucough said:**
> This time it didn't even run slowly, just failed completely. What's all this avahi business and where did the weird inet addr come from?

I checked out the above mentioned stuff and it transpires that it's an ip address set up when no others connect... but the DNS settings for my ISP are there in the DNS list for the network configuration. .. which managed to connect before, albeit at a snails pace. How odd!

---

### Post by ModelM on 2008-07-18
Maybe this won't work, but I'd like to be able to cross it off the list...

High error counts are often caused at the hardware layer - a bad or intermittent network adapter, for example. If possible, try a different cable between the computer & router. Even if this cable works fine elsewhere it might be hurting us here. Cables can be damaged in ways which aren't apparent. Even if the cable is not damaged the tiniest variable can make a difference - even the fit of a particular plug on a cable into the receptacle of a certain networking adapter. (I had that situation once - fought it for days & was about to call in an exorcist...)

---

### Post by phucough on 2008-07-18
> **ModelM said:**
> Maybe this won't work, but I'd like to be able to cross it off the list...

High error counts are often caused at the hardware layer - a bad or intermittent network adapter, for example. If possible, try a different cable between the computer & router. Even if this cable works fine elsewhere it might be hurting us here. Cables can be damaged in ways which aren't apparent. Even if the cable is not damaged the tiniest variable can make a difference - even the fit of a particular plug on a cable into the receptacle of a certain networking adapter. (I had that situation once - fought it for days & was about to call in an exorcist...)

Okay, I'll see if I can give it a shot tomorrow. Thanks.

---

### Post by phucough on 2008-07-18
Spot on, mate.

Just tried it with the other PC in the house and it was fast as F.

Thanks so much! :guitar:

---

### Post by casevh on 2008-07-18
This sounds like a problem with negotiation of the speed/duplex settings between the network card and the port in the router.

What is the output of "sudo ethtool eth0"? 

On my system....

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes

casevh

---

### Post by phucough on 2008-07-18
casevh, it's just been sorted.

Thanks for your help though.

---

### Post by phucough on 2008-07-18
Hang on, just realised what you were talking about...it's a follow on thing right?

Sorry, a bit drunk right now, long (but fun!) night. Just kickin back with a few tunes and bit o the tinternet.

I'll check out what you said tomorrow :)

---

### Post by phucough on 2008-07-29
> **phucough said:**
> Hang on, just realised what you were talking about...it's a follow on thing right?

Sorry, a bit drunk right now, long (but fun!) night. Just kickin back with a few tunes and bit o the tinternet.

I'll check out what you said tomorrow :)

I actually realised when sober that it wasnt a follow on thing and an alternative solution. Just thought Id mention it - cheers for everyone's help though :)

---

### Post by Jive Turkey on 2008-07-29
I noticed in your ifconfig outputs that your MTU was 1492.  I think this needs to match the MTU setting in your router, and usually the defaults are 1500 (mine is anyway).  I suggest matching those up and if that doesn't solve it, try reducing the MTU to 1300 or something.  

What kind of wireless chip do you have?

---

