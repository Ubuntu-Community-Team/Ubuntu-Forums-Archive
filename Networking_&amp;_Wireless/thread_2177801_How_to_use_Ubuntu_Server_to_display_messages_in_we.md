---
title: "How to use Ubuntu Server to display messages in web browser automatically"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by coss-cat on 2013-09-30
Hello Everyone,

I would like to do the following (searched the internet before posting here with no success though):

Premises:
- i live in a small block of flats and i have a thinkpad X61 laptop that runs Ubuntu server 12.04 LTS 
- I have a fiber optic net connection that allows me to share some of my net to my 3 neighbours (already did it :smile:)
- unfortunatelly because of a design matter, I am the one that holds all block's comune facilities (water pump runs from 
my electric current; outdoor lights as well etc.) so i am the self procalimed "administrator" (which i hate a lot !!!)


Solutions that I seek forward:

- given the upwards facts I need to do something that displays each time my neighbours open a browser a message
that they need to pay an amount of money for the past month replacing my "admin" atributes. I can do the logic to
calculate the montly fees, but don't know how to do the thing with displaying stuff in browser. I saw this to some 
internet providers that anounce you with few days before how much you have to pay for a given month.
- I need to do something also to control dinamically the throughput that gets to each of my neighbours; meaning that when
only one is connected he will get full speed of internet, when someone gets connected too, the first one will be limited and 
the band will split to 2 etc.

I am ready to modify everything including buying an aditional lan card (insert in PCMCIA) and transform the Ubuntu server 
into a router etc. 

Small description of the network I have:
Fiber gets into my house where there is a Media Converter (MC) that converts to wire (RJ45); From here I plugged this wire into
a wireless router (D-Link DI-524; very old ... will be changed soon with an other one). From here, each of my neighbours get a 
UTP cable into their house, where a wireless router is installed. Resume: From my router that gets signal through WAN port I
send through 3 wires from LAN ports signal to 3 WANs of 3 different routers



Hopefully you got the idea. 

Thank you all for suggestions and have a nice day.

cosscat

PS. i posted the same thread here:
[http://ubuntuforums.org/showthread.php?t=2177591](http://ubuntuforums.org/showthread.php?t=2177591)
I reposted here because thought that for the second part networking is more appropriate.

---

### Post by Malcolm_Reynolds on 2013-10-10
Hi there, this is my first time posting to these forums, and I'm very new to Linux/Ubuntu. However, the answer to your post doesn't really have much to do with Linux, it is pretty much just all networking, which I'm very good with.

Ok so I'm just going to say this: This is MASSIVE project, to do something on the scale that you are talking about. It isn't really a case of just a script that writes to text files... This is a whole integrated system that; to be sturdy, efficient and viable, is very very complex. However, it is a very awesome idea, if you have the time and dedication to impliment it, hell go for it because this sounds awesome.

Basically there are a few things I would take into consideration first:
- This is the most IMPORTANT point: Check with your ISP that you are allowed to do this, becuase I'm not quite sure that it would be. I think from the ISP's point of view it'd be, "If they want internet through us, they have to pay us." Which right away makes doing it behind their back very risky. Especially if you plan on making any money from this, which I would highly recommend to cover costs of installs, UTP cables, and the 'labour' of creating the system. Just check with your ISP, I doubt this is fully legal, but you never know.

- As far as I can see aswell, for 3 people, this isn't very viable. To do something this big for 3 people (4 including yourself, but I doubt you want to tell yourself that you need to pay x amount), just isn't really worth it. Just keep a spreadsheet of it or something and keep track of how much they owe you manually. Sure doing it manually takes time and isn't nearly as fun, but I think it would take you far too long to set this all up than it's worth. Just for the sake of a few minutes a week sorting out a spreadsheet. That being said, if you are planning anytime soon to expand to the rest of your building, sort of anywhere between (10-20 people/apartments/neighbours) and your whole apartment block would maybe start to make this viable, depending on how long you spend working it out manually a week AT THAT POINT.

I would say this now, your current setup is perfectly adequate if you plan to do this for the forseeable future. You really don't need to go throwing away any money at this point on router servers or anything like that. I would however invest in 2 things, even if you don't want to do the whole automated system you are talking about. These two things are:
- A gigabit router (10/100/1000 b/g/n) that has QOS (Quality of Service) functionality and about 10 or 12 ports. Your router now might even be able to do QOS now. All QOS is, is limiting bandwidth through certain IP ranges so that is what you want when you say you want even service for all your neighbours. If you're not too bothered about exact even bandwidth for all your  neighbours, then a Switch should be fine (Switches don't support DHCP,  so you can't reliably set up QOS against IP addresses that may change)  as the whole bandwidth will split itself between whoever's using it  anyway. So on such a small scale, you don't really have to worry about  QOS so much. DHCP is definately a must though. But you can just connect your router and the switch, then plug all your neighbours into the switch. I'm only saying this because of correctness and scaleability. I'm guessing your router at the moment only has a small amount of LAN ports, and a bigger router or switch would give you a lot more.

- Also for admin reasons and neatness reasons, I would set up each of the routers that you have in your neighbours apartments to different Subnets from your router. So that say Neighbour X has their router as 192.168.1.1 (on your network), and all the devices from their router will just be 192.168.1.xxx. Then for Neighbour Y, make their router 192.168.2.1, then everything that connects to their router as 192.168.2.xxx. This would however require you to manually set up each of your neighbour's routers on a static IP, but that would just be a one time thing.

I'm sorry, that probably isn't the answer you wanted straight away, but it is a big project, sounds very fun, but huge nonetheless. if this post hasn't put you off, I am happy to answer any questions you have.

tl;dr: If you only plan on having a small handful of people connected to your internet then just keep a small spreadsheet of it all, that is the easiest/quickest option, easy to set up and not very time consuming at all I'd imagine. If you plan on trying to grow and don't mind a lot of work - read the whole post. Also check with your ISP if this is legal - THIS IS THE MOST IMPORTANT PART.

---

