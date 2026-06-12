---
title: "Running 2 routers with 1 ISP?"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by z.s.tar.gz on 2008-07-14
I have a problem. I have a desktop downstairs and a newly built home server upstairs. I have 2 routers, a no-brand-name one the ISP gave me, and a Zoom one I got myself.
The problem is, when I turn the one upstairs on, the one downstairs loses connection, and with it, every wireless device in the house.
I really need both to have Internet, but I don't know if the ISP even permits that or what is going on. I'll admit I'm a noob when it comes to how the internet works.

I've attached a **very crude** drawing to show where I'm at.

---

### Post by pytheas22 on 2008-07-14
My ISP only lets me have one router connected to the Internet at once...that way I'd have to pay for a second connection if I wanted to connect two routers.  If I try to plug in a second router, it doesn't work.  You may want to ask your ISP if its policy is the same.

Maybe there's a solution to the problem, however, if we know what your needs are.  Why do you want to use two different routers?  Are both of them wireless?  If the upstairs router is not wireless (as your drawing seems to indicate), would it work to buy a cheap wireless card for the machines currently connected via the wire?

---

### Post by issih on 2008-07-14
Yeah, I'd agree that you are trying to do something unsupported.

You really should only have one router connected to the phone line. That's the whole point of a router, to allow more than one pc to access the web through the same isp connection, that is its job, they exist specifically because doing what you are trying doesn't work.

Your simplest solution is either to snake a network cable from the upstairs pc to the downstairs router, or buy a wireless dongle for the upstairs pc.

Other options exist if you are trying to limit the number of devices occupying the wireless, powerline networking for example.

Hope that helps

---

### Post by z.s.tar.gz on 2008-07-14
I wanted to run a small server with LAN instead of wireless, but I guess I can't.

The problem is that the downstairs router only has 1 eternet out.

But I'm thinking about replacing that one with the other Zoom one, because it has 4 outputs, and just putting the server near the desktop.

The only problem I see is:
Can one computer connected to it have a dynamic IP and one have a static IP?

---

### Post by e24ohm on 2008-07-14
I am not sure about your brand of routers, but it depends on the felxability of your routers. You could run RIP, or even static routes to the networks you are trying to implement.

Which router has yoru broadband modem connected? Most likley it is dropping out because of routing protocols, and your ISP.

---

### Post by freetree on 2008-07-14
I think you can use the Zoom one router instead, and have one computer run wired and the other one wireless. And yes, you can setup one computer with static IP, and the other one with DHCP.

---

### Post by dca on 2008-07-14
Would bridging them solve your issue?  I mean in one of my wireless routers which is fairly new, it has the meat & potatoes of bridging in the webmin utility...
 
[http://www.ehow.com/how_2091726_bridge-wireless-routers.html](http://www.ehow.com/how_2091726_bridge-wireless-routers.html)

---

### Post by dca on 2008-07-14
...wait a moment, I just re-read, are you saying upstairs is a wired router and downstairs is a wireless router?

---

### Post by pytheas22 on 2008-07-14
> The only problem I see is:
Can one computer connected to it have a dynamic IP and one have a static IP?

I assume that you want this because you want one computer to always have the same IP.  If so, any decent router should have an option in its configuration utility to assign certain IP addresses to certain computers--i.e. you should be able to say, "The computer with MAC address AB:CD:EF:12:34:56 should always receive the IP address 192.168.1.2."  That way you can still use "dynamic" IPs served through dhcp on the whole network, but in effect the IPs would be static, in the sense that they'd always be the same for each machine.  This would probably be a simpler solution than trying to use static IPs for part of the network and dhcp on the other part.

---

### Post by issih on 2008-07-14
Actually using static ips and dhcp is dead simple. the router will define a starting ip address and a pool size, e.g. 192.168.0.50 and a pool size of 50

All dhcp assigned addresses are then in the range 192.168.0.50 -> 192.168.0.100

So you can merrily assign any ip outside that range statically and all will be fine.

We are all assuming here that both your routers are adsl modem routers (based on your diagram). Technically if one of them was a cable router you could probably chain them from each other, but the benefit to you would be very small as you would still need a wire going from upstairs to down.

You can certainly use the zoom router (assuming it is an adsl modem one) to replace the isp provided one, but based on your drawings it isn't a wireless router, so you will lose that functionality. to that end, you may be able to just chain a network switch from your existing router to get both the wireless and multiple hardline ports.

---

