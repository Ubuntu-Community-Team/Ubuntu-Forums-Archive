---
title: "Frustration is sometimes a good thing, it clears the head."
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by bbrand on 2007-01-25
I have a old P1 (gulp) running Redhat 7.3 as my server/router/gateway/firewall/printer server/etc.

I got a “new” old computer (P3) and am building this to replace the “old” one (age is relevant when you pass 50). I am going to utilize Edgy on this system as I have been running Ubuntu on my personal desktop for some time (the other three desktops here at home run XP) and am reasonably happy. Especially the forums and wealth of information from some excellent folks has helped me out of some really tight spots.

The building of the server has been hit and miss. VNC was an issue, took me a day to get that up and running (finally went for x11vnc). Samba took several hours until I found where things were going wrong.

I am not configuring my ADSL Ethernet modem; pppoeconfig did not work (I think the modem is too old for that one). So I figured out how to get pon, poff and plog to work and set up a connection. But, a connection without a firewall is silly of course, and that is where I been struggling.

My server has three artifacts: eth0 (connected to the modem), eth1 (connected to the routers) and of course ppp0 running for the DSL. I tried Firestarter for the firewall because I wanted something different than the IPTABLES scripts I have been using. Whatever people say, the IPTABLES syntax is archaic and if you do not tweak it daily easy to forget. I am forever struggling if I want to change things so a GUI based firewall seemed heaven sent. 

First of all, Firestarter was a big mistake, it took me the better part of a day to understand that Firestarter will not work with three artifacts, only two. The resulting IPTABLE always prevented one of the artifacts from taking part. So anybody with this situation or wanting to set up a DMZ: do not use Firestarter (unless someone can point out where I am wrong that is ...).

I am almost tempted to go back to scripts and IPTABLES, but want to give it one more try. fwbuilder seems to be a alternative, it seems to cater for more than two artifacts. There must be more intuitive ones that set up IPTABLES easily. If not I am tempted to build one with TCL/TK. How hard can it be? 

I am open to suggestions: GUI based firewall, which one?

Ben

---

### Post by ewankho on 2007-01-25
I did not understand 80% of your post (being a newbie) but maybe you could try GuardDog.

---

### Post by bbrand on 2007-01-25
Thanks Ew, had a quick peek and it seems interesting. 

Anyone have experience with this one?

Ben

---

### Post by DerHesse on 2007-01-25
Why don't you get yourself a hardware router. It's not really expensive if you compare it with it with your energy costs for an extra pc.

Think about it!

---

### Post by bbrand on 2007-01-25
DerH, you are of course right if that was the only thing I was using the server for. It is also a Samba server with lots of disks attached, a printer server, it servers our scanner, the picture collection, BitTorrent downloads, our music collection and takes out the garbage ;-)

As I have the server it make sense to use it in this fashion, even though it takes time to set up and figure out. Frustrating as it is ... it is fun!!

thanks
Ben

---

### Post by koenn on 2007-01-25
I'd suggest using iptables anyway. 
I've used a number of (commercial) hardware firewalls that clearly were using some sort of embedded Linux with iptables - on one hand, The had a GUI but their "user frendly" translation of iptables syntax was such that i could see iptabbles lurking in the background. At the same time, that userfriendly GUI sometimes obscured things  - I found that simply applying iptables a lot sipmler than trying to figure out what exactly the GUI was trying to tell me. : you just go "I need this and that sort of traffic to go from here to there" and replace the sorts of traffic with port numbers, and de 'here' to 'there' with lan or jost ip addresses. 

Although I've never used it, I'd expect that any iptables GUI front-end could in some way obscure things and dumb them down (like : not being able to deal with more than 2 network cards). Besides that, having to get  iptables rules right  helps you understand how networks interconnect and how computers communucate. Usefull skills for someone who's playing with network connections the way you seem to be doing. 

Of course, you're entitled to your own choices so don't consider this a "use the ******* command line" post  :)
But is I don't use GUI firewalls, I can't help you in that department.

---

