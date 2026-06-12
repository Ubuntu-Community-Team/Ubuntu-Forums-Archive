---
title: "Can't connect to internet using adsl modem"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by faintscrawl on 2009-06-19
I'll try to keep this brief.

When I had windows I had my computer wired to a Netgear Router, then modem, to my phone jack. It'll all worked.

When I switched to Ubuntu a year ago I was delighted to find that the computer connected to the internet with the same set up as above with no problems and absolutely no configuring needed.

Now--the last two weeks--I'm having some issues--slow and intermittent browsing of internet. It's the same on my ubuntu machine and my wife's windows laptop that accesses the Netgear wirelessly. 

I thought it was the ISP's fault. They say no. The phone company also checked the situation and they see no problem. These guys think it's my router or modem. So I want to take the router out of the set-up and see if the internet access is better if I run straight from my machine to my modem. I changed the wiring and created a dsl connection using the network manager (entered my username and password), but it won't connect to my isp. It says "Wired Network Disconnected". If I put the wiring back to the way it was (through the router) and connect with "auto ethernet" connection, as usual, I can get back online (with my usual patchy service.)

So basically I need help connecting to the internet through a dsl modem. It's a SPeedstream 5260. I've been working on this for about 8 hours, reading, tinkering, but getting nowhere.

Thanks.

---

### Post by faintscrawl on 2009-06-19
Nevermind.

I solved it.

The solution was so easy I would be embarrassed to reveal it.

:)

---

### Post by FreewheelinFrank on 2009-06-19
As far as I can see, it should just be a case of taking the LAN plug out of your router and plugging it directly into the the LAN port of the modem.

[http://bc.whirlpool.net.au/bc/hardware/?action=h_view&model_id=112](http://bc.whirlpool.net.au/bc/hardware/?action=h_view&model_id=112)

Your modem seems to be ADSL 1, so you might get a speed improvement upgrading to an ADSL 2+ modem/router.

Or your ISP could just be lying. They do that sometimes.

---

### Post by faintscrawl on 2009-06-19
Thanks for the tip about the modem. I might try to get the isp to upgrade me, even if it's not the problem.

My mistake was that I was entering my username wrong. I hadn't entered it for years. Thought I knew it, but I checked on my router to see how I'd configured two years ago and immediately saw my mistake.

It's too early to be sure but so far things do seem okay without the router, so it may be that  it's flaking out sometimes.

---

### Post by markbuntu on 2009-06-19
Your router could have a virus or all your neighbors are using it. I reset mine once and within an hour I had 8 neighbors trying to use it, and they all have their own. I had to add some security so I could get better speed for myself.

---

### Post by Sudat Tuladhar on 2009-07-28
I am really new to Linux...
I have an Aztech modem and have configured it in a bridge mode..

In Ubuntu 9.04 (jaunty) I just added a new connection to DSL connection under Network Connections and provided my username and password .

(service: Anyname)

Everything was set to default and the modem works just fine for both the ethernet and usb mode....

---

