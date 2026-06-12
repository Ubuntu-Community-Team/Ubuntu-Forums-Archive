---
title: "Newbie networking nasties :("
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by Rykhaard Damian on 2007-05-24
Hey all. It's my first time back here since first joining about 18 months ago. After building a new machine over a 9 month period, I've now decided to almost completely dedicate it to Ubuntu Linux, seeing the troubles looming with Vista and the lack of support for Win XP 64. :sad:

Networking troubles, that I'm hoping I'll be able to create a solution for with help from others as I'm back to square one for learning how to work with Linux. :eek:

Here is the situation overall, for the network / Internet connection hopefuls:

We are connected to the Net from my girlfriend's iMac. (G4 processor in one of the upside down dome shaped machines), through my D-Link wireless router to the cable modem.

This PC that I'm typing on, is wirelessly networked with a D-Link WDA-1320 PCI card.  (32 bit machine; AMD 2700+ w/ 512 meg)

My new machine (AMD XP X2 64 4800+ w/ 1 Gig) has XP 64 and Feisty Fawn installed on it.

1) In my first networking attempt (32 bit machine and XP 64 machine), a direct networking cable between them, wouldn't allow either machine to recognize the other machine.

2) In my 2nd attempt (32 bit and Feisty), Feisty SAW a Windows network ON this (32 bit) machine, but wasn't able to make contact otherwise, no matter what I did on the 32 bit machine. (Setting up a VPN on this one attempted, after advice from coworker at work).

4) 3rd attempt - setting up a VPN on both (32 bit and XP 64 OS), still wouldn't get me anywhere - leading my thoughts to requiring a HUB between the 2 machines, in order to invert the network connection between the 2 machines.

5) 4th attempt - I pulled the WDA-1320 wireless PCI card from this (32 bit) machine and plopped it into the XP 64 machine. It wasn't recognized at all.
Further research at D-Link found that they have no drivers for Win XP 64, and will NOT be providing any drivers for that OS, at all. (Linux drivers are provided at "your own risk".

My question being now: can any of you out there tell me, whether I can expect to be able to wirelessly (required) network my XP 64 machine, with my girlfriend's Mac, that's located upstairs from me? I'm fully willing to go out and purchase another wireless router as well as PCI card for my XP 64 machine, if required. I wouldn't have any troubles following instructions if they're located in a Wiki and / or Forum (relating to Feisty Fawn) somewhere. :smile: I've been searching over a few days period in my attempts to network all 3 of these machines, with no success for the XP 64 machine at all. I'd much rather get the XP 64 machine (via Feisty) networked, than this current 32 bit machine, as I'll eventually be phasing this one out of use.
Also - with usage comparisons and all that I've read - I would much rather stick with Ubuntu, than be faced with the lack of abilities and speed capabilities that I'd be limited to via Vista. (As well as it's COST! :sad: :sad: )

Any help will be greatly appreciated! :grin: Here I am wondering - why it took me 18 months to come BACK to Linux / Ubuntu. From all that I've read in the Forum so far - I wish I hadn't left, in the first place. :wink: (One piece of software kept me in Windows. Now that I'm not using that software anymore - I've nothing else left TO keep me in Windows! Yay. :grin: LOL )

Take care all,
Warmth and Peace,
Ryk

---

### Post by scrooge_74 on 2007-05-24
Your post is rather long and stopped reading half way throught.

Let me see if I can clear things up.

You have a cable modem, which then has a wireless router connected, the router should assign ips to every machines so everybody is in the same network.

You are attempting to go the long and confusing way of doing things.  Stick to the wireless router, which probably has  ethernet ports in the back for  any Pc which does not has wireless card.

Example, at home I have 3 laptops all wireless, but I can stil connect them by the ethernet ports.  At the office have one wired PC and one wireless as I type.

AS for seen the PCs inside the network that is step two after you have them all online. Since I dont have knowledge on MACs dont have a clue how to make the PCs look at each other, i think if Io remember well there is something in linux call apple talk that came installed as default in Debian but I think you have to install in Ubuntu which is use to talk to MACs

---

### Post by Rykhaard Damian on 2007-05-24
The wireless router that's connected between the iMac and Cable modem has to remain where it is, as her iMac is the Gateway to the Internet from this house.  My machines are here in the basement - thereby requiring me to stick with a wireless network.  (She wont allow a wired network to run through the house).

My biggest lack of find so far, is a wireless PCI network card that works on a 64 bit motherboard, with Linux running.

Ryk

---

### Post by Rykhaard Damian on 2007-05-24
Update idea:

I'm currently downloading the 32 bit version of Feisty Fawn.  Since the 64 bit version, recognized a Windows network on this 32 bit machine, I'm going to see if it's possible to network 32 bit Feisty with 64 bit Feisty, through a standard non-inverted network cable.  (Whilst having the wireless on the 32 bit machine, networked with the iMac upstairs.)

Here's to hoping - once the DL is complete. :)

Ryk

---

