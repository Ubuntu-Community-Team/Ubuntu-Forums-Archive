---
title: "How would I set up a second network card to have internet+network?"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by Dawnshadow on 2006-09-17
I found out that my dorm banned routers this year, so I was Googling for alternatives so I can keep my laptop-desktop networklet up. (Desktop runs Linux, laptop is on Windows due to the wireless card issues.) Since I already own a crossover cable, the most cost-efficient thing to do would be to simply get behind the desktop and cable swap every time I wanted to transfer files, which would be annoying. 

The second cheapest thing would be to install a second Ethernet card in the desktop and figure out how to do a network through that, so one card would have a normal cable running to the wall and the other the crossover cable into the laptop. (Connection sharing would be nice, but not essential; they've promised wireless access by the end of the calendar year.) The problem is, although several websites say it can be done, none of them actually explain how to do it. Is there a name for this process that I don't know? Can anyone explain how I would do it once I go buy the second card or give me a link to a tutorial? (A windows-based one is fine; I'm sure I could translate....)

---

### Post by amohanty on 2006-09-17
see if this works:

[http://ubuntuguide.org/wiki/Dapper#DHCP_Server](http://ubuntuguide.org/wiki/Dapper#DHCP_Server)

am

---

### Post by Dawnshadow on 2006-09-17
Thanks. I'll try it... um, after I buy and install the second card. ._.; Nice to have a start point, though.

---

### Post by Danieliozzi on 2006-09-17
Install the second nic .boot ubuntu .install firestarter , run it and u will get "internet conection sharing"  .there is a lot of thing that can go wrong in between those steps , but i think that in most of the cases those simple steps can work . 

clues = 
 "ifconfig eth1 xxx.xxx.xxx.xxx netmask 255.255.255.0" to check if the 2nd nic is working
 "lspci" to check if the nic is recognized in case the step above fails

feel free to correct me (anybody) if i'm wrong or if i'm giving the wrong aproach to the problem.

---

### Post by Azyx on 2006-09-17
> **Dawnshadow said:**
> I found out that my dorm banned routers this year

I just wonder how they could bann routers and do not internetsharing makes your computer to a router?

---

### Post by Dawnshadow on 2006-09-18
> **Azyx said:**
> I just wonder how they could bann routers and do not internetsharing makes your computer to a router?

Easy. The rulebook bans routers, not connection sharing. It's *technically* not a router so I'm in the clear. :)

(Besides, the router ban is, as far as I know, aimed at people who bring in wireless routers and don't secure them, allowing any random person use of the university's resources.)

---

