---
title: "Sharing wireless internet via ethernet.."
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2007-03-14
Here's my situation:

My internet goes into my Modem/Router combo.

The family PC is hooked up via ehternet [wired down].

My PC is via WLAN, my PC is hooked up to my Wired down router hooked up to my other PCs running various OSes, Linux included.

Can I get my internet on all those PCs, I think the Windoze sharing only lets PCs w/ WinXP go on...

Is there an app I can run in my system tray to share the internet so ANY PC w/ Ethernet can use it?

---

### Post by Mr. C. on 2007-03-14
I read this three times, and I'm confused by what's connected to what.

Here's what I understand:

1) internet via cable modem/router
2) Family PC connects to 1
3) ???

I'm lost with your PC - you say it is wired and wireless.  Please fill in 3 for me.

MrC

---

### Post by drefined on 2007-03-14
... i am also lost :lolflag:

---

### Post by RealG187 on 2007-03-14
My Modem and first router are combined, it was WLAN and wired down, the family PC is wired into it...

My Computer has a WUGUSB [or something like that] adapter and I have internet on it.

My computer is plugged into the other computers through a router, I wanna get internet on those and they dont have wireless, but they are connected to mine which does!

---

### Post by Mr. C. on 2007-03-15
I don't mean to be critical, but do you have any idea how unclear your descriptions are?  We cannot read your mind, nor see your setup.  We have to rely solely on your description, and it is very confusing.

Let's try it one more time.

Give a name to each PC, and use that name, not "my computer", "my computers" or "those" and "they" (how many do you have ?)

Give a name to each router or modem/router you have.

Tell us exactly what which PC's name is connected by cable (lose the "wired down" jibberish).

Its easy... like this:
* Modem-Router1 is connected to internet.
* PCFamily is connected to modem-router 1 by cable.
* PCSlowPoke is connected to WirelessRouter2.
* WirelessRouter2 has 4 Ethernet cable ports.
* PCLigthning is connected to ...

Again, I don't mean to be critical; just trying to help you clarify yourself so we can help.

MrC

---

### Post by RealG187 on 2007-03-15
Internet comes into modem/router combo 1 [Router 1].

Computer1 is wired into router 1, this isn't really significant.

Computer 2 [Mine] has wireless and is connected to Router1 [Router one is both Ethernet and WLAN].

Computer 2 is connected to router 2, which is just ethernet.

Computer 3 us plugged into router 2 as well, but no Router 1.

I want to get internet on computer 2. It would basically connect to computer 2 through router 2, which would wirelessly connect to router one where the modem will connect...

---

### Post by Mr. C. on 2007-03-15
Ok, much better; I think I have it now.

I assume C2 is your ubuntu system.

First, you need to get C2's wireless connection working.  The easiest way to do this would be to unplug/disable the C2 to R2 wired connection first.  Once C2 can access the internet via R1, then we'll go through the steps required to configure C2 to act as a router.

Your configuration as you've describe it is much more complicated than is ideal, but I am assuming you have done this due to the constraints of your house.  Is that correct?  Ideally, you would have R1 provide Ethernet connections to all via a switch, or even via R2.  With the configuration you've described, you are going to have 3 routers, and that is a complex setup until you understand routing.

MrC

---

### Post by RealG187 on 2007-03-15
All but C2 are in the basement, R1 is upstairs so wireless is the only way to go.

On C2, I run multiple OSes, I would prefer an EXE so that way I could use it w/ Windows and Linux [via Wine]

---

### Post by Austin_KW on 2007-03-15
You already have 2 routers and you want to turn your C2 into another router??? And you want to do this for multiple Operating systems on C2???

It can be done; Change the default route on C3 to be the IP for C1 (wrt R2) and enable routing/ICS on C2

But why not just connect the R2 uplink port to one of the LAN ports on R1. Use Ethernet over power if you dont want to run cables. 

/austin

P.S what is the point of R2; where is it routing to?

---

### Post by jglen490 on 2007-03-15
Probably too many routers, REALG187, or not connected in the right sequence.  If router #1 has more than one wired connection, then each ethernet equipped computer can be wired directly to router #1.  If router #1 has wireless capability as well as ethernet, then whatever computers use wifi can standalone and they can each be configured separately.  That's a whole 'nother subject by itself :) .

If router #1 has only one wired connection, router #2 has more than one ethernet connection, then connect router #1 ethernet connector to router #2 wlan input.  Connect your remaining ethernet computers to the outlets on router #2. That MIGHT work.

In my mind, if router #1 has only one ethernet connection, then use a switch with multiple outputs.  That definitely works great.

---

### Post by Austin_KW on 2007-03-15
If you are really determined to do this sharing of your wireless connection, at least you will learn how routing works.

You dont want to be modifying/setting up the routing and forwarding on C2 by hand, get the firewall routing GUI
On C2 enter the following commands in a terminal window
```
sudo apt-get install firestarter
```

then run the GUI
```
 sudo firestarter 
```
This should bring up a wizard,  (if it does not then select the wizard from the menu)
In the wizard
[INDENT]Select your wireless device (probably wlan0) as your internet interface
Enable Internet connection sharing and select your wired ethernet device (probably eth0) as your LAN interface
then save[/INDENT]

Find the IP address (inet addr:a.b.c.d) for eth0 on C2
```
ifconfig eth0
```
This will be you default route address on C3

Go to C3 and change the default route to inet address a.b.c.d
```
sudo route del default
sudo route add default gw a.b.c.d
```

This is off the top of my head, I know it can be done, but I have the feeling I am missing something!

yes; you may have have a default route problem on C2, if you are using dhcp  on R2 you might have to delete a default rout back to R2

---

### Post by RealG187 on 2007-03-16
I cant plug C2 into R1, nor R2 into R2, I am in the basement...

On Windows I can use internet connection sharing, but I only think that works if all PCs are running Windows. So if I do the thing above then It will work if C2 is in ubuntu?

What if  c2 is running Windows?

I was thinking of using C2 as tri OS [98,XP,ubuntu] and then C3 would be my linux machine, when C2 and 3 ran Windows it worked, but when I used DSL on C3 it didn't work and I would assume ubuntu would do the same thing...

---

### Post by Austin_KW on 2007-03-17
> **RealG187 said:**
> I cant plug C2 into R1, nor R2 into R2, I am in the basement...

On Windows I can use internet connection sharing, but I only think that works if all PCs are running Windows. So if I do the thing above then It will work if C2 is in ubuntu?


Yes it does the something similar to windows ICS; turns C2 into a router & forwards internet traffic
> 
What if  c2 is running Windows?

I was thinking of using C2 as tri OS [98,XP,ubuntu] and then C3 would be my linux machine, when C2 and 3 ran Windows it worked, but when I used DSL on C3 it didn't work and I would assume ubuntu would do the same thing...

Not sure here,when it works on C3 what are the IP address and default gateway on C3?

---

### Post by RealG187 on 2007-03-21
I dunno any of the info. I might be able to get the IP adress, but it might differ from Windoze and Linux...

Would there just be an app I can run in the system tray that would route the internet over?

---

### Post by stchman on 2007-03-21
> **RealG187 said:**
> Here's my situation:

My internet goes into my Modem/Router combo.

The family PC is hooked up via ehternet [wired down].

My PC is via WLAN, my PC is hooked up to my Wired down router hooked up to my other PCs running various OSes, Linux included.

Can I get my internet on all those PCs, I think the Windoze sharing only lets PCs w/ WinXP go on...

Is there an app I can run in my system tray to share the internet so ANY PC w/ Ethernet can use it?

From the title of your post you are trying to share wireless over ethernet.  Why?  All you need to do to is get a wireless router, (Belkin, Linksys, D-Link, etc.) all make capable wireless routers for under $50.  You can then institute MAC filtering, WEP, WPA, etc. for security purposes.

This will allow you to share your internet (wired and wireless) to all your family.

---

### Post by RealG187 on 2007-03-21
But I only have Wireless on my one PC! [my PSP has too, but that's a different story], there are only 2 PCs on, the one wired in, and my Wireless one...

---

### Post by stchman on 2007-03-21
> **RealG187 said:**
> But I only have Wireless on my one PC! [my PSP has too, but that's a different story], there are only 2 PCs on, the one wired in, and my Wireless one...

Yes, EACH PC that you want to have wireless access must have a wireless card installed.  You can buy wireless PCI ethernet cards for around $25 and install them.

You only need one router to do everything you want.  If you have more PCs than ports on your router than install a switch  in one of the router ports.

Lets not make home networking more complex than it already is.

---

### Post by fearevilleet on 2007-03-21
Why dont you just buy a wireless router? They are usually cheap usually under $30. This way the internet sharing is not dependent on a computer being on.

---

### Post by Austin_KW on 2007-03-21
I think they want to do it because they can, not 'cause it is the easiest/best way to do something. It is not something that you would recommend to a new user or someone building their first home network.
 But some of us do these thing to learn how to build a router/NAT/bridge etc. If you understand the principles it aint that complex. Then you can build your own routers, firewalls, proxies, web caches & filters, traffic policers, VPNs et al, and all for zero cost. Part of the joy of a linux system.

---

### Post by RealG187 on 2007-03-22
My brother only has usb 1.x [dont think thats an issue cuz thats like 14Mbbs, and my internet is only 3..]

But my Moms PC, doesnt have any USB, neihter does my [Macintosh](http://en.wikipedia.org/wiki/Performa)

---

### Post by stchman on 2007-03-22
> **Austin_KW said:**
> I think they want to do it because they can, not 'cause it is the easiest/best way to do something. It is not something that you would recommend to a new user or someone building their first home network.
 But some of us do these thing to learn how to build a router/NAT/bridge etc. If you understand the principles it aint that complex. Then you can build your own routers, firewalls, proxies, web caches & filters, traffic policers, VPNs et al, and all for zero cost. Part of the joy of a linux system.

I will 100% agree with the learning portion.  As for zero cost lets see.

Cheap PC ~$400 ($150 even built form used spare parts)
Wireless router ~$50

If someone wants to for the sake of learning I am all for it, but to use a PC as a router is a pretty expensive option.  Not to mention that a PC uses far more electric power and can be less reliable since PCs are far more complex than a router.

If the person wants to make a PC a router he/she needs to enable Internet Connection Sharing (requires two ethernet cards) and make the wireless card the output.  Firestarter is a good program to use type sudo apt-get install firestarter or go to the synaptic package manager to install it as it allows you to do such a thing.

This thread is good for starters:

[http://ubuntuforums.org/showthread.php?t=103881](http://ubuntuforums.org/showthread.php?t=103881)

---

### Post by RealG187 on 2007-03-22
I wanna use my PC as a Touter, since it is on most of the time anywas, I only have one ehternet card, but my Wireless uses USB...

---

### Post by stchman on 2007-03-23
> **RealG187 said:**
> I wanna use my PC as a Touter, since it is on most of the time anywas, I only have one ehternet card, but my Wireless uses USB...

Ok, but you do know when that PC is off any of the other PCs on the network won't be able to get internet.

So you have a USB wireless ethernet card.  Same thing as having one that goes in PCI or PCMCIA.  Just tell the internet sharing to use the wireless as the output.  I guess that the USB wireless will be able to broadcast a signal that other wireless cards can use.

---

### Post by RealG187 on 2007-03-24
> **stchman said:**
> Ok, but you do know when that PC is off any of the other PCs on the network won't be able to get internet.

So you have a USB wireless ethernet card.  Same thing as having one that goes in PCI or PCMCIA.  Just tell the internet sharing to use the wireless as the output.  I guess that the USB wireless will be able to broadcast a signal that other wireless cards can use.


My PC is mostly on, if my bro wants to go on he can go on his [If I can get this working, if he wantes to go on when I am not on, he can just use my PC...

How can I get this working, I got it once.. Now it doesn't work at all...

---

### Post by RealG187 on 2007-09-13
Can this be done? What if I get a wireless router, can I reverse it?

---

