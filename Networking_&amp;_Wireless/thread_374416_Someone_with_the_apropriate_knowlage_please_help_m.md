---
title: "Someone with the apropriate knowlage please help me share my internet conenction"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by DjDarkman on 2007-03-02
I can`t belive no one can give me an exact answer on how can I share my internet connection if I have two ore mor network cards.

In windows it`s just a few clicks ,and I know it`s easy to make it here too ,but no one tells me exact what to do ,

"maybe firestarter can do it"
"I think guidedog can be of help"
"google it"

These are NOT answers to my problem.

I need eighter an iptables script that I can start during boot or a program that can do such thing.

Can someone help me on this or is this ownly possible in windows?

btw : I`m not a newbie ,I`m just irritated that no one can answer an important question like this ,net sharing is very important in small and big networks.

---

### Post by chggr on 2007-03-02
Check out this topic. I think your questions will be answered:
[http://ubuntuforums.org/showthread.php?t=366347](http://ubuntuforums.org/showthread.php?t=366347)

---

### Post by DjDarkman on 2007-03-03
> **chggr said:**
> Check out this topic. I think your questions will be answered:
[http://ubuntuforums.org/showthread.php?t=366347](http://ubuntuforums.org/showthread.php?t=366347)

No that doesn`t help I don`t want to make a proxy server ,I want to just set the gateway and dns server on my laptop to the apropriate and have internet on it ,is this impossible?

---

### Post by ellis rowell on 2007-03-03
Right, so I AM a newbie to Ubuntu.

Under Windoze I used a 3Com wireless modem/router. My link was with wireless card (desktop) and USB wireless dongle. Changing to GNU/Linux I have not yet been able to use these to connect, but have connected both machines via ethernet cable. Well, it's one way round it.

---

### Post by Soarer on 2007-03-03
Yes - it's easy under Windows. But you must understand that the reason it is so easy is that Windows is so insecure, and sharing a connection on Windows is very unsatisfactory if you care about security..

Ubuntu by default (I believe) blocks all insecure connections, like from an internal-facing NIC to an Internet-facing one, so you need to either edit IPTables (which you will need to understand first) or use a software firewall (like Firestarter, Smoothwall or Shorewall which I use) to edit IPTables for you, to ensure the connectivity you want is allowed in your system.

Install a firewall from the repos (people say Firestarter is easy, for a firewall :)) and try it. It's not hard, but for good reasons it isn't easy either.

---

### Post by DjDarkman on 2007-03-03
> **Soarer said:**
> Yes - it's easy under Windows. But you must understand that the reason it is so easy is that Windows is so insecure, and sharing a connection on Windows is very unsatisfactory if you care about security..

Ubuntu by default (I believe) blocks all insecure connections, like from an internal-facing NIC to an Internet-facing one, so you need to either edit IPTables (which you will need to understand first) or use a software firewall (like Firestarter, Smoothwall or Shorewall which I use) to edit IPTables for you, to ensure the connectivity you want is allowed in your system.

Install a firewall from the repos (people say Firestarter is easy, for a firewall :)) and try it. It's not hard, but for good reasons it isn't easy either.

I rather bare the security risk than need to pay another ISP for internet connection ,I think this is logical ,btw It`s not insecure ,because it`s only for the internal network ,not the outside world.

Firestarter doesn`t know what is a pppoe connection ,and I`m not an unix administrator to learn all those iptables commands and settings and why learn them if I need to do one simple task?

Ok so this means that there is no solution exevpt to buy a router (wich is too expensive for me) or buy another PC and install windows on it (wich is way more expensive)?

---

### Post by perfidious_alban on 2007-03-03
> **Soarer said:**
> Yes - it's easy under Windows. But you must understand that the reason it is so easy is that Windows is so insecure, and sharing a connection on Windows is very unsatisfactory if you care about security..

Sorry but that kind of sniping does no good whatsoever. I've had a wireless Win network running, without problems, for over four years. The router is firewalled, the PCs are also firewalled and running AV programs. I'm now on week 3, and my third network card, trying to get Ubuntu 6.06 to behave as it should. In that time, I've twice had an Internet connection which was lost on re-boot. 'Tweaking' files following *recommendations* from various sources have resulted in an unstable machine requiring a fresh install. If I didn't have plenty of time on my hands and wasn't so determined, I'd probably have done as I have several times over the last eight years and given up on Linux.

So last night I tried 6.10 ! Ooops, 'no root partition defined' despite having used the drop down box to specify a format and overwrite of the partition 6.06 is on.

I came to the conclusion about twenty years ago that *ALL* software can produce problems, so please let's not knock one to cover up for the deficiencies of another.[/QUOTE]

---

### Post by chggr on 2007-03-03
> **DjDarkman said:**
> No that doesn`t help I don`t want to make a proxy server ,I want to just set the gateway and dns server on my laptop to the apropriate and have internet on it ,is this impossible?

You want to set your laptop to be a DNS Server or you want to enter the IP of the DNS Server and Gateway?

If you want to do the later, click on System -> Administration -> Networking -> DNS 
To set the Gateway, click on the Properties button and set it there.

I am pretty sick of listening to people saying that Windows is far more easier and everything works there and linux sucks. Well, have you thought that windows are easier because **we are used to it.** Just think of that: Your first PC was a Windows or a Linux PC? How many years have you spent learning Windows  and how many learning Linux?
If you are used to something, it is sometimes very hard to change, even if this change means more security, stability and less trouble.

What I'm trying to say is that we must be reasonable and not fear to change...

---

### Post by DjDarkman on 2007-03-03
> **chggr said:**
> You want to set your laptop to be a DNS Server or you want to enter the IP of the DNS Server and Gateway?

If you want to do the later, click on System -> Administration -> Networking -> DNS 
To set the Gateway, click on the Properties button and set it there.

I am pretty sick of listening to people saying that Windows is far more easier and everything works there and linux sucks. Well, have you thought that windows are easier because **we are used to it.** Just think of that: Your first PC was a Windows or a Linux PC? How many years have you spent learning Windows  and how many learning Linux?
If you are used to something, it is sometimes very hard to change, even if this change means more security, stability and less trouble.

What I'm trying to say is that we must be reasonable and not fear to change...

You missunderstood me ,I want my PC to give internet to my laptop ,I want it to have an ip ,for example 10.0.0.1 ,and if  I enter that ip on my laptop as a gateway and DNS server ,it should have internet.

I`m not lazy to try things out ,but if no one helps me ,I can`t do nothing ,this is an essential task I want my PC to do ,I don`t think it`s so complicated ,that no one can answere me.

For examople if me and a few friends live in the same aparment ,it`s logical that we rather share one internet than everyone of us to pay an ISP.

But I still don`t understand why won`t anyone help me?is it so hard?

---

### Post by chggr on 2007-03-04
OK! Are you talking about wireless connection or ethernet connection (using a router or a switch)? This stuff is information that we need in order to help you set up your computer. If you don't supply us with the appropriate info, how are we gonna give you advice?

---

### Post by DjDarkman on 2007-03-08
> **chggr said:**
> OK! Are you talking about wireless connection or ethernet connection (using a router or a switch)? This stuff is information that we need in order to help you set up your computer. If you don't supply us with the appropriate info, how are we gonna give you advice?

ethernet connection with a switch.

---

