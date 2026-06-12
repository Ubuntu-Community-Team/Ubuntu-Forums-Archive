---
title: "Ethernet Hub to split signal to two machines"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-01-29
Now I have two computers working.  I want to get them both on the Internet.

The screenshot is of the Ethernet Hub I got at Best Buy, should this work for me, right out of the box, or what?  They sent me home with one cable, shall I see if I put the hub between the modem and the computer if it works.  I would be trying one computer at a time, well, because I didn't bring home two of these cables.

---

### Post by halitech on 2010-01-29
a hub will work if your ISP provides you with 2 IPs. If you don't get 2 IPs from your ISP then you will need to either a) buy additional IPs from your ISP or b) purchase a router instead of a hub

---

### Post by Chris Edgell on 2010-01-29
Thank you, halitech, I guess I'll call and ask what an additional IP costs.  Do THEY care if you get a router?

---

### Post by bowens44 on 2010-01-29
routers are cheap, probably cheaper then paying for mulitple IPs. you should be able to get a router for not much more then you paid for the hub.

---

### Post by falconindy on 2010-01-29
I'll add the following, assuming that your ISP does indeed give you multiple IPs.

I would advise against getting a hub (as opposed to a switch), let alone a 10mb one.

The functional difference between a hub and a switch is as follows. In a hub, the bandwidth rating (10mbit in this case), is the maximum amount of throughput the device can handle, split across all links. This means if you have 3 devices attached to the hub and all 3 are asking for throughput, each will only be allotted 3mbits.

A switch overcomes this handicap and is able to supply the full link speed to each individual link.

I notice in that same screenshot is an advertisement for a 10/100 switch for only $7 more. It's well worth it.

---

### Post by halitech on 2010-01-29
the companies I have dealt with normally charge between 5-10.00 a month per additional IP. Depends on who "They" are. Some will not allow you to get a router, most take a "what we don't know doesn't bother us" attitude. 

If they don't care, get a router as you can get a decent router for around 50.00 which will pay for itself within 5 to 10 months.

---

### Post by Chris Edgell on 2010-01-29
So the switch would do the job and then I wouldn't need a router?

---

### Post by lijcam on 2010-01-29
You will be better off getting a router. It will make it much easier if you add other devices to your network in the future. Most come as a modem/router single unit these days. If your modem has feathers like DHCP, firewall and NAT etc then it is already a router and you could simply plug it and the computers in the hub.

---

### Post by halitech on 2010-01-29
> **Chris Edgell said:**
> So the switch would do the job and then I wouldn't need a router?

who is your ISP right now and what modem do you have?

---

### Post by Chris Edgell on 2010-01-29
AT&T and I have a Motorola modem Style MSTATEA,
it does offer a website for advanced modem configuration, if that matters.

lijcam, that's what the guy at Best Buy said I should or could do, plug all into the hub.

---

### Post by lijcam on 2010-01-29
The sales guys is right under the assumption that your modem has routing capabilities. All a modem basically does is convert your ISP delivery method eg ADSL, Cable, etc to Ethernet.

I think it would be best to spend a few extra dollars and get a four port router instead most come with wireless as well there days.

---

### Post by Chris Edgell on 2010-01-29
Better than the switch then?

---

### Post by lisati on 2010-01-29
> **Chris Edgell said:**
> Better than the switch then?

Short answer: yes!

A router generally has more "intelligence" built in than a hub or a switch, and many routers have firewall capabilities.

---

### Post by lijcam on 2010-01-29
Yes they have a switch included in them. A basic home router has the capability to act as modem/router/switch

If you spend a bit more you can also get wireless build in and usb so you can plug in a usb hard drive.

I would recommend something along these lines.

[http://www.bestbuy.com/site/Linksys+-+Wireless-G+Broadband+Router+with+4-Port+Ethernet+Switch/8741365.p?skuId=8741365&id=1202648529130](http://www.bestbuy.com/site/Linksys+-+Wireless-G+Broadband+Router+with+4-Port+Ethernet+Switch/8741365.p?skuId=8741365&id=1202648529130)

---

### Post by Chris Edgell on 2010-01-29
lijcam,

and this one shown "here" for about $50, is the one with the wireless built in and usb?

---

### Post by lijcam on 2010-01-29
It has wireless but not the usb. I found the ones with usb are still unjustifiably too expensive.

Here is a example of one with usb.
[http://www.bestbuy.com/site/Linksys+-+Dual-Band+Wireless-N+Gigabit+Router+with+4-Port+Ethernet+Switch/8892335.p?id=1215819613183&skuId=8892335](http://www.bestbuy.com/site/Linksys+-+Dual-Band+Wireless-N+Gigabit+Router+with+4-Port+Ethernet+Switch/8892335.p?id=1215819613183&skuId=8892335)

---

### Post by Chris Edgell on 2010-01-29
Oh, yeah, THAT jump took my breath away.  I'll go for the other one.

Thank you all very much.  You've provided an invaluable assistance.

Oh, I'll still need those cables, won't I? (Don't laugh too much if I ask how wireless is it???)

---

### Post by lijcam on 2010-01-29
Before you go and buy that exact one you may want to see what others on the net have to say about it. Other brands have similar hardware at that price and you may find they work better under certain conditions. 

For example some cheap routers cannot hand lots of concurrent open connections so if you do use services such as bit torrent it may slow to download and or crash. I had a Netgear router like this and would crash after 30 minutes of using bit torrent. I also had a Linksys that was flaky and would lockup randomly, this was fixed with firmware updates but was very annoying.

---

### Post by Chris Edgell on 2010-01-29
Good of you to mention all this.  And it's good for me to give these things a little time.  Yeah, I'll slow down some and see if I get any other opinions on this.

Thanks, lijcam

---

### Post by lijcam on 2010-01-29
> **Chris Edgell said:**
> Oh, I'll still need those cables, won't I? (Don't laugh too much if I ask how wireless is it???)

It is the 802.11G wireless so thats 54mbit theoretical max speed but you will get about 7mb in day to day use which is fine for surfing the net and light file transfers. If you need to move a large amount of data say 1Gb I would do it over a wired connection.

802.11G is also supported by most smart phones these days so iphones, Google phones, N97 etc. Also the xbox360 (via adapter) ps3 and wii all support it.

Most routers these  day come with lots of cables but you may want to check in the box before purchasing. Extra cat5e cables should cost no more the 2-5 dollars depending on length.

---

### Post by penguinv on 2010-01-29
Chris,

Here's a good discussion about 
   "What is a -- vs a ---?": hub, switch, router.
[http://ask-leo.com/whats_the_difference_between_a_hub_a_switch_and_a_router.html](http://ask-leo.com/whats_the_difference_between_a_hub_a_switch_and_a_router.html)
But an overview is this one
[http://ask-leo.com/how_should_i_set_up_my_home_network.html](http://ask-leo.com/how_should_i_set_up_my_home_network.html)

Wikipedia has relevant pages for each:
[http://en.wikipedia.org/wiki/Ethernet_hub](http://en.wikipedia.org/wiki/Ethernet_hub)
[http://en.wikipedia.org/wiki/Network_switch](http://en.wikipedia.org/wiki/Network_switch)
[http://en.wikipedia.org/wiki/Router](http://en.wikipedia.org/wiki/Router)

If you dont need the wireless or dont need it fast, and $$ are and issue, then consider getting an older wireless modem, used.
If it only does wireless B then it becomes worthless in the consumer market and it will work just fine as a router, if I understand it well.

Thanks for bringing this up in my mind. I had never gone there.

---

### Post by egalvan on 2010-01-29
OK, my .04 worth

That 10BaseT (10Mb/sec) Hub for $25 is grossly over-priced for such an obsolete piece of gear. Best Buy should be ashamed.
It should be  in the Bargain Bin Section, for $5.00

Your DSL Modem *APPEARS* to be a router.
googling turned up this...

Motorola 2210-02 ADSL modems act as NAT routers providing local addresses via DHCP when shipped.
---------------------------------
and this...

Your Motorola 2210-02 has LAN address 192.168.1.254.
-----------------------------------------------------


If this is true, then all you NEED is a switch.
Ask for an simple, inexpensive SWITCH that has four or five ports.
Preferably 100BaseT (100MB).
Preferably NO DHCP (routing, or NAT), to keep things simple.
This should run $20-$30.

If your DSL MODEM is NOT DHCP-capable, then ask for the same as above, 
but that ALSO has DHCP (routing, or NAT) capabilities.
This should run $30-$50

Wireless is nice, solves the "were do I run the wire" problems,
but can bring it's own set of problems "how do I keep unwanted equipment from logging on"

I ran a pair of CAT6 to each room in my house.
(small house, 800sqt :) )

---------------------------------
[B]if you don't have the manuals,
two locations for the manual[/B]

[http://www.netopia.com/support/hardware/manuals/SoftwareUserGuideV77-Clsc.pdf](http://www.netopia.com/support/hardware/manuals/SoftwareUserGuideV77-Clsc.pdf)

[http://office.manualsonline.com/ex/thread/view/idThread/2034712](http://office.manualsonline.com/ex/thread/view/idThread/2034712)

----------
To give you some ideas, but
**PLEASE NOTE, THESES ARE ONLY EXAMPLES OF EQUIPMENT**

[http://cgi.ebay.com/DLink-D-Link-DI-604-4-Port-Broadband-Router-Switch-NEW_W0QQitemZ190347033105QQcmdZViewItemQQptZCOMP_EN_Routers?hash=item2c51913a11](http://cgi.ebay.com/DLink-D-Link-DI-604-4-Port-Broadband-Router-Switch-NEW_W0QQitemZ190347033105QQcmdZViewItemQQptZCOMP_EN_Routers?hash=item2c51913a11)

[http://cgi.ebay.com/Linksys-Cable-DSL-Router-w4port-switch-BEFSR41-V-2_W0QQitemZ110482997884QQcmdZViewItemQQptZCOMP_EN_Routers?hash=item19b94cc27c](http://cgi.ebay.com/Linksys-Cable-DSL-Router-w4port-switch-BEFSR41-V-2_W0QQitemZ110482997884QQcmdZViewItemQQptZCOMP_EN_Routers?hash=item19b94cc27c)

-----------------------------
My home set-up consists of 
DLS MODEM with (DHCP) ROUTING capabilities...
...connected by one CAT5 cable to...
1000BT SWITCH (8 ports)...
....connected by CAT6 cable to various machines and switches.

And a final note...
DSL MODEM is a misnomer.
It **should** be DSL ADAPTER.
Modem stands for MOdulator/DEModulator,
and refers to analog/digital signal transformations.
DSL is digital all the way. Which why the phone companies had to install new equipment.

---

### Post by Chris Edgell on 2010-01-29
Thanks for being so thorough, I should have known it wouldn't be simple OR easy.  I will try to spend some time studying...although so often I just don't get it, but I'm gonna' try.

I did put my modem between the computer and the hub.  All the lights stayed lit on the modem (power, ethernet, dsl, internet) but I wasn't online...it seemed to act like a router to the hub.....

I am thinking about it not being a modem, but an adaptor.

Everytime I turn around, I am so over my head.  The best I can say is I'm trying.
I am trying.

"Once you add a second computer to you're faced with setting up a network, at least to share the internet connection."  This is all I have really wanted, to share the internet connection...(I thought I could buy some $10 splitter).

---

### Post by egalvan on 2010-01-29
> **Chris Edgell said:**
> Thanks for being so thorough, I should have known it wouldn't be simple OR easy.
  I will try to spend some time studying...although so often I just don't get it, but I'm gonna' try.

It **is** easy, if you have an honest, competent computer technician available. 
But they can be as rare as honest auto mechanics... :)

You may (or may not) find better support at a Mom&Pop computer store/repair shop.
Another place to look is a local Linux User's Group (LUG)
( hint...try this link...   [http://www.linux.org/groups/](http://www.linux.org/groups/)  )
A regular college-type computer club is another.
The college computer "science" course is another.
Take the manual for your DSL thingy and let them have a gander at it.

-----------------------
> I did put my modem between the computer and the hub.
  All the lights stayed lit on the modem (power, ethernet, dsl, internet) but I wasn't online...it seemed to act like a router to the hub.....


Wall Panel connected to the DSL Filter* (one cable)
DSL Filter* connected to the DSL "MODEM" (one cable)
DSL "MODEM" connected to the switch/router/hub (one cable)
from there, one cable to each machine that wants to be networked.
(*note, you may or may not need the DSL filter.
some modems now have them built in)

-----------------------------
> I am thinking about it not being a modem, but an adaptor.

In the old days, modems were connected to the phone lines...
so the term stuck.
Semantics, and the popular press got it wrong.
Hacker versus Cracker
Geek versus Nerd
Modem versus adaptor.

> Everytime I turn around, I am so over my head.

Shoulda seen me when I first laid eyes on a computer...
IBM 1130 Mini-Mainframe...
Nineteen Sixty and Nine it was...
freezing rain, sun so hot, uphill both ways... :D

Seriously, let me state the obvious.

**EVERYBODY STARTS AT THE BEGINNING**

>   The best I can say is I'm trying.
I am trying.

And that is, indeed, the BEST thing.
Keep On Keeping On.

---

### Post by Chris Edgell on 2010-01-29
I am repeating a sentence I put in in an edit...

Once you add a second computer to you're faced with setting up a network, at least to share the internet connection.

So the two points I want to bring out here are:  1) if it isn't obvious, at this point all I want is to share the internet connection (at minimal cost); and 2) I was a little encouraged to think that my "modem" could serve as a sort of router to the hub and that I could plug both computers in THIS hub.  I was very heartened to see all four lights light up..... I don't know why I WASN'T connected to the internet in actuality...could I have been very close but something just needed some configuring to get it going.

When I did go and read some of those articles ABOUT THIS hub, it sounded like it could require some tech support to get it going.  WAS I CLOSE? It does seem so because when I had to get some tech support from ATT the main thing they were after was having all 4 of those lights lit up.

Have I gone off track here?

---

### Post by lisati on 2010-01-29
> **egalvan said:**
> Shoulda seen me when I first laid eyes on a computer...
IBM 1130 Mini-Mainframe...
Nineteen Sixty and Nine it was...
freezing rain, sun so hot, uphill both ways... :D


Ah, nostalgia! I got to touch one once in 1980 - it had punched cards for breakfast, contemplated programs in the RPG programming language for lunch (that's "**R**eport **P**rogram **G**enerator", not role-playing game), and printed the output for afternoon tea. (I'm a bit off with the timing here, didn't get much - officially "none" - experience driving the thing.)

---

### Post by egalvan on 2010-01-29
Great Zot!! RPG!!

I mind one "program" that ran some 20-24 hours.
Non-stop.
And if interrupted, had to start from the beginning.
Many ran six hours.


InSkel
Skel
asm
FORTRAN
COBOL
RPG
SPICE

Oh my!

4Kilobyte Core
expanded with 4Kilobyte Expansion Core.
300,000 operations a second.
500,000 word hard drive capacity
LP80. The line printer that printed 80 lines a minute (theoretically)
Console. The IBM Selectric Ball typewriter that hit 10cps
.
Oh My!

Four years of that!

Oh My!

What a Blast!
Yes, I really did enjoy it.
Yes, I really miss some aspects of it*.
Really.

*flashing lights, lots of them.
switches, lots of them.

---

### Post by Chris Edgell on 2010-01-29
egalvan, here are the facts you asked for, about my computer and my modem.

no manual, no CD only ATT tech support.
style: MSTATEA
# above the bar code: *2210-02-1002*
Sticker: for advanced modem config.
go to:[http://192.168.1.254](http://192.168.1.254)

I am using a desktop running Ubuntu,
connected via DSL

chris@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:74:2e:21:5b  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe2e:215b/64 Scope:Link

---

### Post by audiomick on 2010-01-30
hi Chris.
I gather you got your test computer up and running.

You are dealing with a problem that everyone has, and  everyone has problems with it.

I will try and explain a couple of concepts for you, which I think will help you understand what all the boxes do.

To start with, what comes out of the phone line?
There is a single complex electrical signal in there that contains 2 different signals. That sounds hard, but it is not. You can always picture what is happening with electrical signals by imagining waves in water. The physics is the same.

So, imagine waves coming into the shore. You have big waves and little ripples all mixed up. The signal in the pone line is the same, effectively.
The filter that has been referred to just sorts out the big waves from the little ripples. The phone wants the big waves, the computer wants the little ripples, and the filter makes sure that they each get what they want without being disturbed by the others.

The modem, or adapter, is like a translator. If you imagine that the signal in the phone line is in morse code, then the modem turns it into "english" for the computer, and turns the "english" that the computer speaks into "morse code" before it goes into the phone line.

The question of what a router, switch or hub does is like distributing mail.
With a hub, it is as if the postman just dumps a bag of mail on the floor and leaves it to be collected. It is all available to every one, but no one is doing any sorting.

A switch isn't all that different. It is still all available to everyone, but the postman is standing by making sure that there are no fights. It all works a bit more smoothly and faster.

A router is like when someone sorts through the bag and gives each person his mail individually and takes their mail and makes sure it gets where it is going to.

The router can deal with internal traffic as well as external.
Imagine a hotel: the porter (router) accepts mail from the postman and delivers it to the rooms. He also accepts mail from the rooms and gives it to the postman. He also accepts mail from the rooms and gives it to other rooms.
What the postman brings and gets is the internet traffic, the room to room stuff is like your local network, i.e. traffic between 2 computers in your house.

So to put it together:
The filter sorts out the right signal from the combination that is coming out of the phone line and passes it on to the modem.

The modem, or more correctly adapter, translates the signal into something computers understand.

The router directs traffic: "sorts the mail"

A hub/switch makes everything available to everyone, whereby a switch does it better.

---

### Post by Chris Edgell on 2010-01-30
Oh, very good analogy.  I needed that.  

I haven't solved the BIOS problem on the tester so am trying to hook up my original so that I can dare go into the BIOS of THIS one to get the messed-up tester to match.

So began at Best Buy with the Geek Squad telling me if I have a good modem it actually IS more of a router, so all I"d need is a hub.  (Actually the explanation came from lijcam in Post 8 of this thread.)

My question now is based on this:  When I hook-up the hub between the modem and the computer all 4 lights come on.  (Power, Ethernet, DSL, and Internet...the 5th one is labeled "activity" and only shows intermitent flicker anyway.)

I have to go out now, just wanted to get this in-thanks again audiomick.

So, with all things considered (by you), does that prove that the modem DOES work as a router and the hub is providing the "jack" to hook up more that one machine?  In which case there would be some other adjustment to be made to get it to work, because as it is...even with all the lights on, the machine is still offline.

---

### Post by Mike'sHardLinux on 2010-01-30
Hi Chris!

That modem is capable of doing some very basic router functions. But, there is no guarantee, at this point, that it is actually configured to behave that way. I work with a LOT of AT&T DSL and they usually have their modems configured in bridged mode, which means no router functionality. *You can call AT&T tech support and ask them if this is how they have your modem configured.*

As far as the lights on your modem, it does not guarantee that the modem is set up to do any routing. The INTERNET light does suggest that it is set up for PPPoE, but that could mean it is doing some routing, or it could mean it is set up in half-bridged mode, which means it is doing authentication (PPPoE), but NOT any routing. 

An easy test would be to connect both PCs to your hub and see if they can both access the Internet.

---

### Post by audiomick on 2010-01-30
> **Chris Edgell said:**
> 
I haven't solved the BIOS problem on the tester 
Oh well, good luck then...


> So began at Best Buy with the Geek Squad telling me if I have a good modem it actually IS more of a router, so all I"d need is a hub.  (Actually the explanation came from lijcam in Post 8 of this thread.)
I don't know the model myself, but a quick bit of searching seems to support this.

> My question now is based on this:  When I hook-up the hub between the modem and the computer all 4 lights come on.  (Power, Ethernet, DSL, and Internet...the 5th one is labeled "activity" and only shows intermitent flicker anyway.)

The lights tell you
Power : obvious - the device has power and is switched on
Ethernet : there is something plugged into one of the ethernet ports.
DSL : the phone line is being detected and is alive
Internet : a connection has been established with your internet service provider.
the "activity" one will always flicker a bit. The ports talk to each other, like "here I am" "me too, I'm still here too". This shows up as activity. You will see, when it is up and running, that when you download something, for instance, this will light almost constantly.

> So, with all things considered (by you), does that prove that the modem DOES work as a router and the hub is providing the "jack" to hook up more that one machine?
I don't want to say "prove". It would seem so, and I think so...


> In which case there would be some other adjustment to be made to get it to work, because as it is...even with all the lights on, the machine is still offline.


That's the thing: On a hub, there is nothing to adjust. Theoretically, if you have a connection when you are plugged directly into the modem, it must still work with the hub in between, at least as far as I know...

Here is something to try:
You said that the modem has a web style control interface. I assume this means you have looked at it, which means you know the IP address for the modem. That would be the address you enter in firefox to get the control interface. According to your post earlier, it is 192.168.1.254 , i.e. the default address of the modem.
If you haven't changed it, it should be that.

So, take the hub out of the setup, i.e. computer direct to the modem. 
In a terminal, do
```
ping 192.168.1.254
```

the command "ping" sends an answer request to the address you give. It will run all day if you don't stop it. To stop it, use ctrl + c
you will see something like

```
mick@ubuntu-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.241 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.232 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.223 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.257 ms
^C
--- 192.168.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.223/0.238/0.257/0.016 ms
```

If the address is wrong, or there is no connection, it returns
```
mick@ubuntu-desktop:~$ ping 192.168.0.50
PING 192.168.0.50 (192.168.0.50) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Host Unreachable
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=5 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable
From 192.168.0.3 icmp_seq=7 Destination Host Unreachable
^C
--- 192.168.0.50 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7009ms
, pipe 3
```

If you have internet, and the address right, you must get a positive from "ping". 

Once you have that, plug the hub in between again, and try again. This will show you if the hub is providing the connection between modem and computer at (almost) the most basic level.

---

### Post by Mike'sHardLinux on 2010-01-30
Chris,

I just read some more of your previous posts, and there are a couple of issues to fix, first.

1)
I noticed that you said you have the modem between the hub and your computer. You should connect it like this:
DSL phone line --> modem --> hub --> computer(s)

2) 
With that hub, you need to connect the Uplink port to the DSL modem. 


Now, see if you can access the Internet.....

---

### Post by sdowney717 on 2010-01-30
search for wireless routers on ebay.
wireless N is better than G is better than B
you really want a 4 port wireless router 

cheap one right here
[http://cgi.ebay.com/D-Link-Airplus-Extreme-G-Wireless-Router_W0QQitemZ320478814771QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item4a9e06a233](http://cgi.ebay.com/D-Link-Airplus-Extreme-G-Wireless-Router_W0QQitemZ320478814771QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item4a9e06a233)

[http://reviews.cnet.com/routers/di-624-airplus-xtreme/4505-3319_7-20817312.html](http://reviews.cnet.com/routers/di-624-airplus-xtreme/4505-3319_7-20817312.html)

---

### Post by audiomick on 2010-01-30
> **Mike'sHardLinux said:**
> 
I noticed that you said you have the modem between the hub and your computer. You should connect it like this:
DSL phone line --> modem --> hub --> computer(s)

2) 
With that hub, you need to connect the Uplink port to the DSL modem. 

Good call, Mike.
I didn't pick that that up...;)

---

### Post by sdowney717 on 2010-01-30
Routers are daisychainable. And configurable as HUB or Router
I have a cox cable modem, it takes the signal and converts it into an Ethernet Internet output.
Plugged in next I have a VOIP router with one in and one output port
Plugged in next I have a Gateway 4 port wireless G router, plug the output from voip router into internet WAN port of gateway router.

My computers connect to the LAN ports of the gateway router.
I ran an 80 foot ethernet cable downstairs from the gateway router LAN port into a Netgear 4 port wireless G router. That one downstairs is set up as a HUB only. I plug in a computer downstairs into the Netgear router that is functioning as a HUB.

The Gateway wireless router hands out the IP adresses to all my connected devices which are downstream of itself.
The Gateway wireless router gets its IP from the VOIP router.
The Linksys VOIP router gets its IP from the cable modem
The cable modem gets is IP from COX

---

### Post by Sir Jasper on 2010-01-30
Hi,

May I enquire if these are the two almost identical computers that you were talking about recently? If so, do you want to transfer programs/date between them or do you have another reason for wanting dual internet connection.

There might be better/cheaper methods of obtaining your goal if you explain your needs. My apologies if you have already supplied details - I only browsed some 2/3rds of the posts here.

My regards

---

### Post by JKyleOKC on 2010-01-30
> **Chris Edgell said:**
> Oh, I'll still need those cables, won't I? (Don't laugh too much if I ask how wireless is it???)For wireless to work with your two Dell desktop machines, you'll probably have to add wireless cards to both of them -- and the cost might take your breath away again.

I'm currently in the midst of researching something very similar for my middle son; his wife is a medical transcriptionist and has just started for a new company. They provided her a computer to use in working from home, but no networking gear to go with it so she's having to provide that herself. The problem is that her home office is upstairs, and their home modem-router setup is downstairs. Running cable all over the house isn't an option so we have to figure a way to set her system up for wireless, without opening the company-supplied computer and installing a wireless card.

As it happens I'm with AT&T also, and their multiple-IP services are much more costly than single-IP residential service. I'm paying $79.95/month for my five IPs; that's the smallest multi-IP plan they offer. In addition they list a $250 setup fee to switch to the plan.

Compared to a router at $50-$75, the choice is fairly obvious. I have a Linksys WRT54G that's worked well for me, but the first one I bought failed within a week and this one is its replacement. My main router, however, is an Xubuntu system! It took me more than a week to get it set up properly so I don't recommend that you try to do this, at this stage. Your best bet would be an inexpensive router that has at least four LAN ports (wireless capability won't hurt but should probably be turned off to prevent neighbors from using it without your knowledge).

Be very wary of believing advice from Geek Squad and Best Buy clerks; most of them seem to be under pressure to generate more sales, and many of them have even less technical knowledge than you yourself (though they won't admit it). Use the forum here for tech questions, instead...

---

### Post by Chris Edgell on 2010-01-30
Well, now...(like Craig Ferguson)...what have we learned today??!!

I've learned a lot -- I thank you all!

Some comments and conclusions:  Not to seem defensive, BUT I stated it incorrectly in Post #23, which I corrected in #30..When I said I put the modem between the computer and the hub..that would have been impossible anyway because there is only one Ethernet connection point in the modem.

Sir Jasper if you'll read #25 only and then I'll just say here all I want is for both computers to be online at the same time.  Anything I could want to do I could do by going back and forth but that seems like a lot of wear and tear - all that shut down and start up, don't you think"?  As I've said when I began this phase, I thought I'd be going out and paying about $9 for a splitter.  Ask me any specific question you want, I'll answer -- you are a good follower of my "case" and I appreciate it too.

I did check out the ping with the cable regular setup and got what you said, audiomick or Mikehardlinux.  In the setup through the hub with all four lights lit up, all I got was, like, "No internet connection", so my modem must be half-bridged.

sdowney717, I'll keep Ebay in mind.

Thanks Jim Kyle, we shall see what happens next.  I've started 3 project now and all have left me back at square one.  Well, but a little smarter; a little bigger base of understanding.  I'll let you know if I get to square two anywhere.  (I do have an urge to open a thread about the BIOS but just off-hand can anyone tell me any great study sites on the subject so that I can know something BEFORE asking question to you here.?)

Again, I thank you all.

---

### Post by audiomick on 2010-01-30
Hi Chris.
Keep your chin up, you'll get there.
Remember "ping". It is, in my opinion, the single most useful thing in setting up network stuff. If you get an answer back, you know you have a setup issue, if you don't, it is a wrong address somewhere or a  wrong connection/bad cable

---

### Post by Chris Edgell on 2010-01-30
Thank you for your continuing support and words of encouragement.     I'll remember "ping".

The best to you Michael...oh yes...Australian in Germany...and you were on the train at 2 in the afternoon.  Ah, life!  Hope you're fine and happy.

---

