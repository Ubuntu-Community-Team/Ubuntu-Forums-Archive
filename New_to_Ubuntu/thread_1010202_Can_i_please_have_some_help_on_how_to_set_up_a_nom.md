---
title: "Can i please have some help on how to set up a nome network?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by hyperhopper on 2008-12-13
hello!

in our house, we have our internet going to a modem, which then goes to a router(linksys model # WRT54GS version 6 wireless g broadband adapter 2.4 ghz)

from the router, 4 computers are connected, filling the 4 slots in the back of it.

however, since then, i have acquired 3 servers to play with and my sister got a computer...


what is the best way to hook them all up to the internet?

the goal is all the computers having a FAST connection.(no cutting corners at the expense of speed)

what do we have to buy to hook everything up?(P.S., i only *need* 1 server, but i do need my sister on the 'net)


any help is appreciated!!!!

---

### Post by cmnorton on 2008-12-13
[https://help.ubuntu.com/community/InternetAndNetworking](https://help.ubuntu.com/community/InternetAndNetworking)  		                   		  		  		 		 			
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/8.10/internet/C/index.html](https://help.ubuntu.com/8.10/internet/C/index.html)

---

### Post by hyperhopper on 2008-12-13
huh?

i just wanna know if i need a hub, bigger modem, or how to "daisy chain" or whatever would help me..... this just tells me how to get computers which are plugged in to connect, but i have 2 that need to be plugged in

---

### Post by cdmike2k8 on 2008-12-13
Is your sister's computer wireless because if it is, then you can use that to hook up her computer.  To get the rest of the servers online you have a couple options depending on how much you want to spend and what types of speeds you want.  You could get a new router with more ports $$$$.  You could get a switch with enough ports and hook that up to router, with all computers plugged into switch $$.  Our you could get a small switch and use it to hook up the servers and one desktop to one connection $.  The downside of the last one is that transferring files between computers connected on the switch to ones connected to the router would be limited speed wise, since the maximum uplink would be 100 MBit/s (10 MByte/s).  I believe the large switch would eliminate this bottleneck, although I am not positive.  A router with the required number of ports would be the best way to to as it would be the cleanest, but that might be a little more expensive.  Good luck, and I hope what I said made since.  Please ask for clarification if it doesn't.

---

### Post by cariboo on 2008-12-13
I would suggest buying at minimum an 8 port switch, and hook it into your network this way:

modem-->router-->switch-->computers 

You'll still have three ports on the router, plus seven more to connect computers to. I've got mine setup that way:

modem-->router-->wireless access point-->switch -->computers.

The access point and the switch are in my detached garage, where my home servers live.

Jim

---

### Post by melojo on 2008-12-13
I would use a switch!!

below is a link that might help.

[http://www.duxcw.com/faq/ics/exprouter.htm](http://www.duxcw.com/faq/ics/exprouter.htm)

---

### Post by hyperhopper on 2008-12-13
A no wireless
B we will spend $$$$$$$$ to get ***_SPEED_***

---

### Post by wmcbrine on 2008-12-13
All you need is a switch. There is no disadvantage, and no speed limitation; I don't know what cdmike2k8 is trying to say there.

Edit: I guess he's talking about a situation where you have (at least) four computers trying to transfer at full bore, but with two of them on either side of a switch, they could be limited by the uplink between the switch and the router. (If it's less than four computers, the limiting factor would be the computers' own network interfaces, so the switch wouldn't enter into it.) In reality, this situation will almost certainly never arise. Most of the time, the network is idle, so each computer <-> computer transfer should get near full speed.

Worst-case scenario, just put the computers that talk to each other the most on the same switch(es).

---

### Post by melojo on 2008-12-13
> **hyperhopper said:**
> A no wireless
B we will spend $$$$$$$$ to get ***_SPEED_***

Just buy a new 8 port router if you have the money!!!

---

### Post by hyperhopper on 2008-12-13
oh ive been reading, and a switch is like a splitter that is faster than a hub
?

---

### Post by Old_Grey_Wolf on 2008-12-13
Linksys has this group switch [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175243274305&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7430533028B58](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175243274305&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=7430533028B58).

A router with more ports to replace your old one may be almost the same price.

---

### Post by agathian on 2008-12-13
Well, when you say "SPEED" what exactly are you referring to?

computer -> internet 
or
computer -> computer

If this is a cable modem or DSL connection - your speed will be limited by that anyway.  If i am not mistaken, the connection between your router and computer would atleast be 10M, if not 1G.  typicaly cable modem, DSL connections, hover around 1-2M..

Depending on the configuration of the computers and what you plan on doing with them - converting some of them to wireless would probably a good thing.

If this  all needs to be hardwired, get either a switch or a hub, say 5-ports, and connect it to one of the ports in your existing router/switch.

Nowadays, 5-port switches are not that costly, so go for it, unless you have a hub lying around.

Again - it all depends on what you are going to be doing with these computers - typical home use, this should be more than sufficient.

---

### Post by hyperhopper on 2008-12-13
by speed i mean comp --> internet

and agathian, i dont understand your second paragraph
> If this is a cable modem or DSL connection - your speed will be limited by that anyway. If i am not mistaken, the connection between your router and computer would atleast be 10M, if not 1G. typicaly cable modem, DSL connections, hover around 1-2M..


---

### Post by hyperhopper on 2008-12-13
just curious, will switches

A slow down the connection

B if one person downloads alot, will it slow others down?


A is the most important

---

### Post by hyperhopper on 2008-12-13
opps! sooryy  everytime i refreshed it was sending it again.....


my apologies.....

---

### Post by hyperhopper on 2008-12-13
just curious, will switches

A slow down the connection

B if one person downloads alot, will it slow others down?


A is the most important

---

### Post by melojo on 2008-12-13
> **hyperhopper said:**
> by speed i mean comp --> internet

and agathian, i dont understand your second paragraph

Your internet provider will limit your download and upload speed.  Where I live DSL providers have packages ranging from 1.5 to 6.0 m Download speeds.  Cable on the other hand is between 3.0 to 10.0 m.  Also, how far away the server is from you and the bandwidth it has.   You can go to the link below and test your speed. 

Pick a server closest to you!  You can also pick one farthest away and see the difference.

[http://www.speedtest.net/](http://www.speedtest.net/)

> 
just curious, will switches

A slow down the connection

B if one person downloads alot, will it slow others down?


A is the most important


With a switch you will probably not notice any difference and as for your second question it depends on the speed of your internet.

---

### Post by adaptr on 2008-12-13
> **hyperhopper said:**
> hello!
in our house, we have our internet going to a modem, which then goes to a router(linksys model # WRT54GS version 6 wireless g broadband adapter 2.4 ghz)
from the router, 4 computers are connected, filling the 4 slots in the back of it.
however, since then, i have acquired 3 servers to play with and my sister got a computer...
what is the best way to hook them all up to the internet?
With a switch connected to the router.
You will need at least 6 ports to connect the 4 new computers:
1 connection on the router will go to one port on the switch,
and therefore one of the computers currently connected to the router has to move to the switch.
Switches are commonly available in 5 or 8 port versions, so you will need an 8 port switch.

> the goal is all the computers having a FAST connection.(no cutting corners at the expense of speed)
what do we have to buy to hook everything up?(P.S., i only *need* 1 server, but i do need my sister on the 'net)You can connect the home systems all with gigabit etehrnet, but the router will only have 100mbit ports.
Any of them will be many times faster than your internet connection.
Using switches is the fastest possible way of connecting your computers, and until all computers are using all the bandwidth of the network, you will not notice any slowdown on your internet connection.

---

### Post by egalvan on 2008-12-14
OK, as others have noted, you have two different connections to deal with...

1) computer to internet

2) computer to computer


The first will be limited solely by your internet provider.
(unless you manage to buy some *really* old hubs)

You cannot go faster than the pipe into your house.
DSL in my house is capped at 1.5mb. That is the max that I can access the internet.

My internal network... now that is another matter.

My DSL modem is hooked to a hardware firewall/router.

This is hooked to one port of a 5-port Giga-bit switch.

This Giga-bit switch has four Cat-5E wires connected...
one goes to my bedroom, one to my living-room, one to my garage/work-room, and one stays in the computer room.

Each room has a 4-port switch. Two are 100b, two are 1000b.

The bedroom has two computers hooked to its switch...
living-room has one computer hooked to its switch...
garage/work-room has two, sometimes three, computers hooked to its switch...
computer room has four computers hooked to its switch.

Computer-to-computer speeds are fast, especially between any that are 1000b... access speeds are indistinguishable from local hard drive access in all my computers.

Computer-to-Internet is limited to sharing that pathetic 1.5M pipe entering my house.

A bit more theory...

All modern switches (less than, say, 5 years old) are capable of linking any two ports via address learning.
They are capable of bi-directional data transfers.
And most are capable of simultaneous access to all ports.
This all means "no sharing of bandwidth". Full speed for every machine.
So a 4-port Giga-bit switch may be capable of moving 8giga-bits a second.
So slow-downs due to switches are NOT a factor.

Your internet connection is FAR, FAR slower (usually runs about 10% of the internal LAN). And it has to be shared. And nothing you can do will change that.

Unless you have the money to have an OC-type internet connection to your home. :)
One for every computer you want to hook to the internet...:lolflag:

Bad cable installs can wreak havoc with a good LAN, by the way.


And to finish, a friend of mine has TWO cable accounts...
he got tired of sharing that single 10meg pipe with his kids!

ErnestG

---

### Post by agathian on 2008-12-14
> **hyperhopper said:**
> by speed i mean comp --> internet

and agathian, i dont understand your second paragraph


Sorry - i didnt get a chance to check back yesterday. Guess others have answered it. Just in case - basically in terms of network connectivity to internet - your internet connection - cable modem, DSL, etc - will be the bottleneck. Not your LAN connection [ barring ancient hubs, misconfig, etc ].


To answer your question simply.. in the order of preference..

1] Replace your current router/switch with a 8 or 10 port router/switch.

2] Get a new 5 port switch and connect it to your router.


#2 will probably be easier and should work fine.

> **hyperhopper said:**
> B if one person downloads alot, will it slow others down?

Yes, unless your internet connection has unlimited bandwidth.

---

### Post by hyperhopper on 2008-12-17
> **adaptr said:**
> With a switch connected to the router.
You will need at least 6 ports to connect the 4 new computers:
1 connection on the router will go to one port on the switch,
and therefore one of the computers currently connected to the router has to move to the switch.
Switches are commonly available in 5 or 8 port versions, so you will need an 8 port switch.

You can connect the home systems all with gigabit etehrnet, but the router will only have 100mbit ports.
Any of them will be many times faster than your internet connection.
Using switches is the fastest possible way of connecting your computers, and until all computers are using all the bandwidth of the network, you will not notice any slowdown on your internet connection.

> **egalvan said:**
> OK, as others have noted, you have two different connections to deal with...

1) computer to internet

2) computer to computer


The first will be limited solely by your internet provider.
(unless you manage to buy some *really* old hubs)

You cannot go faster than the pipe into your house.
DSL in my house is capped at 1.5mb. That is the max that I can access the internet.

My internal network... now that is another matter.

My DSL modem is hooked to a hardware firewall/router.

This is hooked to one port of a 5-port Giga-bit switch.

This Giga-bit switch has four Cat-5E wires connected...
one goes to my bedroom, one to my living-room, one to my garage/work-room, and one stays in the computer room.

Each room has a 4-port switch. Two are 100b, two are 1000b.

The bedroom has two computers hooked to its switch...
living-room has one computer hooked to its switch...
garage/work-room has two, sometimes three, computers hooked to its switch...
computer room has four computers hooked to its switch.

Computer-to-computer speeds are fast, especially between any that are 1000b... access speeds are indistinguishable from local hard drive access in all my computers.

Computer-to-Internet is limited to sharing that pathetic 1.5M pipe entering my house.

A bit more theory...

All modern switches (less than, say, 5 years old) are capable of linking any two ports via address learning.
They are capable of bi-directional data transfers.
And most are capable of simultaneous access to all ports.
This all means "no sharing of bandwidth". Full speed for every machine.
So a 4-port Giga-bit switch may be capable of moving 8giga-bits a second.
So slow-downs due to switches are NOT a factor.

Your internet connection is FAR, FAR slower (usually runs about 10% of the internal LAN). And it has to be shared. And nothing you can do will change that.

Unless you have the money to have an OC-type internet connection to your home. :)
One for every computer you want to hook to the internet...:lolflag:

Bad cable installs can wreak havoc with a good LAN, by the way.


And to finish, a friend of mine has TWO cable accounts...
he got tired of sharing that single 10meg pipe with his kids!

ErnestG


i have no clue  about some of this.
 so, what is OC type internet?
what would REALLY old hubs do?
so if the spped im capped at is 1.5MB, then if one personm is downloading a HUGE file, i get slowed down?
if i have a million tabs in FF open, will that slow down other people?
will switches slow down the speed to the net?
and what in the world is this LAN system and how does it work
(i was thinking of turning one of the servers into a host that all the computers can save files to and open files from)(how do i do that?)

---

### Post by egalvan on 2008-12-18
> **hyperhopper said:**
> i have no clue  about some of this.
OK, all of us had to learn this stuff. Nobody was born knowing it, so you are in good company...


>  so, what is OC type internet?
Sorry, this was meant as a joke, hence the funny faces and LOL.:)
Short story... OC is a fast, VERY expensive fiber-optic network connection.
Long story... try these links...
[http://en.wikipedia.org/wiki/OC-3](http://en.wikipedia.org/wiki/OC-3)
[http://www.cybercon.com/connection_wan.html](http://www.cybercon.com/connection_wan.html)
[http://searchnetworking.techtarget.com/sDefinition/0,,sid7_gci212685,00.html](http://searchnetworking.techtarget.com/sDefinition/0,,sid7_gci212685,00.html)

> what would REALLY old hubs do?
Well, REALLY old hubs might not even work with Thinnet UTP cable. (standard network cables, the kind with fat-looking telephone connections (8-pin)
They will probably only use Thicknet Coax. Looks like fat (thick) cable-tv stuff.

But the main draw-back to hubs is that they are "dumb" connections.
They can only handle one connection at a time, and only in one direction. This can have a tremendous negative impact on speeds.


> so if the speed im capped at is 1.5MB, then if one person is downloading a HUGE file, i get slowed down?
Yes.
Although to be totally clear, it's not the SIZE of the file.
Surfing web pages will also slow down other users.
It's just that continuous downloads will make the sharing more obvious.
Sharing 1.5MB means exactly that...splitting 1,500,000 bits every second among the users.

> if i have a million tabs in FF open, will that slow down other people?
JUST having tabs open will not slow down any one else...
it's OPENING the tabs... the info needs to be downloaded.
Once it's downloaded and displayed, there is no more data being moved across the Internet pipe, so no more slow-downs for others.
Unless the window has active content, such as YouTube... or music..
this requires downloading data, hence sharing the Internet pipe.

> will switches slow down the speed to the net?
No modern switch (less than ten years old) will cause any NOTICABLE difference in speed to other users on the same network.


> and what in the world is this LAN system and how does it work
(i was thinking of turning one of the servers into a host that all the computers can save files to and open files from)(how do i do that?)

LAN --- **L**ocal **A**rea **N**etwork
basically the computers connected with network cables, and/or switches, routers and such.
 Usually limited to a small geographical area (building... or groups of buildings, such as a campus, or commercial area)

WAN --- **W**ide **A**rea **N**etwork
basically the Internet, although it means any geographically-separated systems.
 Large corporations, educational institutions, government institutions (e.g. military) use WANs.

And yes, you can dedicate one (or more) computers to "serving" files.
I have done this for some ten years, going back to (gasp!) Windows 98.
One dedicated computer, Celeron @ 300Mhz, 128Meg, with an extra 300Meg drive to hold data.
10BaseT switch, with ThickNet backbone to hubs in other parts of my house.
for it's time, it was quite the set-up.

Now I have a dedicated computer, AMD Athlon-XP3200 Barton-Core, 4Gig RAM, and more drives than I can count...
 okay, it's only approx ten at the moment.
1000BaseT Switch, connected via Cat5e to 5-port 1000BaseT Switches in most rooms of my house.
(And for lurkers out there, yes Cat5e will yield GigaBit speeds if installed CORRECTLY.
This means not exceeding pull pressure, minimum radius and minimum strip length. Also using at least Cat5e hardware all around.)


I hope to have illuminated some dark corners of your knowlege, although I may have cast some shadows also...

Any further questions, feel free to ask...
I may take a while to answer, as I just don't log on every day... usually two or three times a week...
heresy, I know.

ErnestG

---

### Post by hyperhopper on 2008-12-22
0.0

ill have to read through the above post again, but for now

A are there some switches that are "faster" than others? (i know this is the case for routers)

B anybody know whats a good place to get a 5 or 8 port switch?

---

### Post by wmcbrine on 2008-12-23
A. Practically speaking, no. If there is any difference, it's not worth worrying about.

B. Any place that sells computer accessories. Again, it's not really worth worrying about. This is a $20 item.

---

### Post by hyperhopper on 2008-12-23
> **wmcbrine said:**
>  Any place that sells computer accessories. Again, it's not really worth worrying about. This is a $20 item.

where? i did a quickie google shopping search and lowest i saw was $60

(would a radio shack sell this?)

---

### Post by wmcbrine on 2008-12-23
[Here's a nice-looking one.](http://www.bestbuy.com/site//olspage.jsp?id=1149206843192&skuId=7907704&type=product)

And yes, Radio Shack has switches.

---

### Post by LowSky on 2008-12-23
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166007](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166007)

$10 and free shipping, you can't go wrong

---

### Post by djsephiroth on 2009-03-09
> **wmcbrine said:**
> A. Practically speaking, no. If there is any difference, it's not worth worrying about.
Actually, there can be a huge difference. A 10Gbps switch is orders of magnitude faster than a 10Mbps switch. Additionally, higher quality switches such as enterprise-class Cisco fare will be faster than your average Netgear or D-Link home or office switch. Finally, support for jumbo frames will make a noticeable difference at 1Gbps speeds.

> **hyperhopper said:**
> 
B anybody know whats a good place to get a 5 or 8 port switch?
Newegg.com or Best Buy, in that order.

> **hyperhopper said:**
> just curious, will switches

A slow down the connection
No.
> 
B if one person downloads alot, will it slow others down?
Yes, but that has nothing to do with the switch. If you have a 7Mbps internet connection and a 1000Gbps switch, you will still connect to the internet at 7Mbps.

---

### Post by Don1500 on 2009-03-09
Just putting this here cause there are some good links I want to find again. Thanks :popcorn:

---

### Post by hyperhopper on 2009-08-05
I have another question on this topic, I just found out that i seem to have a static ip adress, (cant change it with ipconfig/release+/renew    (yes it is windows sadly :(  )     


will  this make a difference, i heard that some ISPs were changing to static ips so that you couldnt use switches in a certain way, will this affect what We are planning?



(i know its been a while, we are gonna get the switch EVENTUALLY-- having some issues at home........ plzdontask)

---

### Post by hyperhopper on 2009-08-06
bump

---

### Post by druca on 2009-08-06
> **hyperhopper said:**
> oh ive been reading, and a switch is like a splitter that is faster than a hub
?

just get a switch. its not that big of an issue. 

you see with hubs, all of the ports share the bandwidth. its old technology. everyone gets everyone else's traffic and if your MAC address is not deemed as the recipient then your computer would drop the packet. that's why its so easy to sniff traffic off of a hub cause hubs broadcast to everyone connected lol.  
good old broadcast traffic. 

switches though, they build a table of MAC addresses and map them to ports they are connected to. This way only packets a computer would get is the ones whose MAC addresses match the destination. 

its smarter than a hub, who just sends everyone packets, and crosses its fingers. 

get a switch. I HIGHLY doubt you would notice any bottlenecking really. it's not like your running enterprise equipment here lol.


also with your ipconfig thing....

that will not do anything. and it is stupid if they are doing something like that. the only thing I have every heard of the ISP's doing is preferring to use the computer's mac address rather than the router. So in that case all you would have to do it bind the MAC address of one of your computers to the router.

---

### Post by hyperhopper on 2009-08-06
well, if everything goes as planned, we are going to run a website to advertise some of the houses that my family has for rent, a total of 11 apartments, and pics of each room, dont know how much thats gonna take..

---

### Post by LewRockwell on 2009-08-06
We'll second the SWITCH over the hub!

.

---

### Post by LewRockwell on 2009-08-06
> **hyperhopper said:**
> well, if everything goes as planned, we are going to run a website to advertise some of the houses that my family has for rent, a total of 11 apartments, and pics of each room, dont know how much thats gonna take..

keep the file size on those images as small as possible to reduce your total bandwidth consumption

you might want to check your contract and your ISP regarding exactly how much bandwidth you are alloted each billing period

you might be surprised...one way or another...

.

---

### Post by LewRockwell on 2009-08-06
of course, Craigslist bandwidth doesn't cost you a thing...

.

---

### Post by Maheriano on 2009-08-06
Don't know why people are making this as difficult as they are. Just because you don't have wireless doesn't mean you can't get it, I have 5 computers on the internet in my house and all of them are wireless, not a single one is plugged into the switch. Whenever I get a new desktop machine that I need to hook to the internet, I go pick up a used Wi-Fi PCI adapter for $10 and pop it in. Presto, internet. So that's your answer, just get a PCI Wi-Fi card and call it a day.

As for speed, you're limited to the bandwidth that your ISP provides you. I have 10 megs down and 1 up, thanks to the supernet here in Canada. So if I have 5 computers online, I can only balance out at 2 megs down per machine. But if one is sitting idle not really doing anything, I can use their allotment on another machine, just as long as the total between all of them is less than 10 down. There's no way to get speeds faster than what your plan allows unless you buy a faster plan.

---

### Post by LewRockwell on 2009-08-06
referencing bandwidth regarding total usage as metered by ISP

it is your responsibility to know what your contract establishes

that includes BOTH download and upload speeds AND also total consumption

[http://en.wikipedia.org/wiki/Bandwidth_(computing)](http://en.wikipedia.org/wiki/Bandwidth_(computing))

.

---

### Post by hyperhopper on 2009-08-06
the router has wireless capability, but the signal doesnt reach where the other computers are.

The only thing We use it for is a Wii

---

### Post by Maheriano on 2009-08-06
You're telling me they're close enough to run a cable to but not close enough to pick up wireless? Is it wireless A?

---

### Post by hyperhopper on 2009-08-06
methinks its G, but there is an option in the router settings to change it to B


also, the rooms are directly above where the router is, my room is above, sisters room is to the side and above

---

