---
title: "Set up a LAN (+internet) with 2 machines, each with 1 eth card"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by ROWDY!!! on 2008-07-12
Hi,
I expect my problem is fairly specific, any help would be much appreciated.
So I'll get right onto it:

 - I have an internet connection in the form of an Ethernet cable coming into my room (I have no access to the extended network).

 - I have a Compaq Presario V6503 laptop running Ubuntu 8.04 (x86_64) with one ethernet port:
```
lspci | grep "Ethernet"
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)

``` - I have a slightly old custom desktop running Debian 4 (x86) also with one ethernet port:
```
lspci | grep "Ethernet"
02:00.0 Ethernet controller" Lite-On Communications Inc LNE100TX (rev 20)

```What I would like to do is connect both machines to each other and preferably both also to the internet connection. Which brings me to my question: What is the best way?
I have considered the following options but I cannot decide which is the best option or whether  they will even work.

1. Direct connection with an ethernet crossover cable? Obviously this cuts out the internet connection which I'm prepared to sacrifice for the occasional reconfiguration. In this scenario I'd prefer to have a static ip on both machines. Does this involve setting up a DHCP server?
(I've half-heartedly tried this but failed - both static ip in network settings and DHCP with "dhcp3-server" on the debian machine)

2. I connect a router (switch?, hub?) on the incomming internet (ethernet cable) connection (is this possible?). Then connect each machine to the router via DHCP?

Thanks very much in advance for replies or further suggestions,

---

### Post by lisati on 2008-07-12
If you go with option 2 (router/switch), you might find that (a) replugging all the time will be eliminated, and (b) it won't matter if you use regular cable or crossover cable (many router/switches autodetect the kind of cable you are using.)

On the other hand, would option 2 be likely to incur the wrath of those who manage the connection you have acailable to you?

---

### Post by superprash2003 on 2008-07-12
option 2 is better!!go for it!!

---

### Post by Maxymillion on 2008-07-12
You need to determine what form the internet is coming to you in. 
e.g. is the ethernet plugged directly into a cable modem / dsl modem? Or is it plugged into a router? Or is it plugged into a server acting as a router? or just a switch? (dont think a switch would share it tho so doubtful)

If its plugged directly to a modem, the new router will automatically share for you. 

Since you mention external network i presume the internet is coming to you from a router already. Easiest would be just to run another cable from the preexisting router. However barring that, I believe you need to bridge your new router to the original router?!. 

Pretty sure bridging is the keyword you want to investigate anyway.

---

### Post by ROWDY!!! on 2008-07-12
Thanks for your swift replies everyone.
To save my network admin the possible frustration for now, I'd like to look into a direct (ethernet cable) connection between the two machines. As I stated before, my efforts to do so thus far have failed.

-Connected an ethernet cable directly between both machines.
In the graphical network manager set the ip such as:
-10.0.0.x
-10.0.0.x
     Set masks such as:
-255.255.255.0
-255.255.255.0
     Set gateway addresses to the other machines ip.
Admittedly that was a stab in the dark and probably a stupid configuration. I got no connection.
Does the wireless network (running) conflict?

Could you offer some advise on setting up this configuration?
Thanks again,

[EDIT]:
After a little more research I think I was on the right track. The configuration I'm looking for is a point-to-point or peer-to-peer network.
I also need to either buy a crossover ethernet cable or modify a normal one?
Also, the debian machine is running gnome 2.14.3.
The network settings on this machine don't appear to provide an obvious configuration option for p2p. Whereas Ubuntu with 2.22.3 does.
[/EDIT]

---

