---
title: "Can I have a router under a router and still connect to router 1?"
date: 2015-09-11
forum: Networking &amp; Wireless
---

### Post by Higgins909 on 2015-09-11
I hope that this still counts as related to ubuntu.
I have a atnt router in a distant place in my house and it wired up to gigabit switch that goes to some ports in the house, one area is my office.
In my office that cat 5e or something comes out the wall and into another switch and then my gaming computer and ubuntu server.

I got a router lying around with dd-wrt lying around somewhere and wanting to use it.
Power likes to go down more then would like and I want a UPS just for my office, but then I get cutoff from any networking when the router goes away.
(Tested unplugging the switch from the router)
I know its possible to setup a router under a router, but is it possible to do it so that-
I can still ssh to things on the other router?

Like I've had it set to some ip like 192.168.1.1 when my network uses 192.168.0.1...
that difference would break the ability to ssh or file transfer to devices on the other router.
...It was something like that when I played with it many years ago.
I have no need for wifi in my office... the router will only be 100mb tho... atleast I have minimal traffic going that way.

Thanks,
    Higgins909

---

### Post by Bucky Ball on 2015-09-11
Yes. Add the second router like any other network device. Plug it directly into the computer first and set its IP address. Then plug it into the router via ethernet cable (cat5). That's it. 

Anything you plug into the second router, configure the network to the gateway, which is the first router. Example setup:

Router 1: 192.168.0.1
Router 2: 192.168.0.2

Make sure the second router does NOT have the same IP as the gateway (first router). The of the second router as a kind of 'USB hub' for the gateway router, expanding its amount of ethernet ports. As long as router 2 is plugged into router 1 as you would plug in any other computer, even at a distance, you're away.

---

### Post by Higgins909 on 2015-09-11
I will be calling the routers 1st and 2nd from now on.
I think I got it to work... but in a different way.
2nd is plugged into the same switch as my computers, into port 1, not WAN.
I setup the ip and gateway like you said and also found a option in my settings to set it as router if it was behind a router, did that.
(seems it was set as gateway default)
It seems to work, but I don't really understand it.
If I unplug 1st I can still connect to my servers and if I unplug 2nd its like nothing ever happened.
2nd pretty much does nothing until power goes out and UPS kicks on. (Don't got a ups yet but its a plan...)

What I don't get is how it knows 2nd is there and to use it to find my servers? because the switch itself doesn't want to direct my ssh request to my server...
even tho I thought it was supposed to be a advantage of a switch over using a hub.

---

### Post by helgman on 2015-09-21
Late to the game but maybe I can shed some light here.

Connecting router2 via LAN-port (not the WAN-port) makes it a switch in this set up. Since you already have a switch in your office I guess that is not the function you are looking for. If you connect router2 via the WAN port then you need to set up the IP network of router2's LAN to a different address space than the one used on router1 (just like Bucky Bill suggested). If you connect via the switch (LAN-port) then it should be the same.

What is the intended purpose of router2? (What is the problem you are trying to solve?)

The answer to that question would maybe make it easier to give you a better answer.

Regards,
Helgman

---

