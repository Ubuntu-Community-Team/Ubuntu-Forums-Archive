---
title: "Ubuntu as an Internet Gateway"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by woobla on 2008-05-04
Hi Guys

I am new to Linux and want to learn.

I have built a Gateway Machine. And I want to use some type of software that I can log network traffic , firewall and most importantly Set bandwith Caps , & Restrictions on a certain IP, or ip's

This is my setup right now
1 DSL Modem/ router with build in 4 port switch (DHCP)
1 Wirless Router (set to access point)

2x Wirless PC's
1x Wired Pc's
1x Wired PC With 3 NIC Cards.

Essentially I want to be able to leave the gateway PC on 24/7.

My Primary goals are
A: Internet Gateway machine / Bandwith management / logging
B: Make it a 24/7 Torrent box as well. 
C: Learn linux, and play around in a desktop environment

So I guess I would like it to run in the background, and been quite easy to set up , manage and leave running

IS UBUNTU for me?

I have tried Clark connect, and It seems good but it is just a firewall package, and I am not smart enough to add other modules too it. I guess I need a 'windows' feel and ease of use.

Or should I just stick to Windows 2003 Server?

Thanks guys.

---

### Post by xyphur on 2008-05-04
Hi there! First of all, welcome to the community!

I personally have been where you are now and after much trial and effort, I found that Ubuntu (and desktop Linux in general) to be needlessly time-comsuming to set up for such tasks. Ubuntu is geared more as a desktop environment than anything. Yes, it'll do everything else that Linux is well-known for, obviously. Serving up webpages, being a database server, etc, etc.. but for such a simple & specific task such as firewall and traffic shaping, there are better-suited alternatives that are quite frankly much easier to set up and administer. One such alternative is m0n0wall, based on FreeBSD. Completely specialized for doing exactly what you're looking for, and a plethora of other loosely related tasks. I recommend checking out the 1.3 release (which is technically still a beta compared to the 1.2xx releases, but in my experience has proved rock solid for 6 months straight). Plus, with 1.3 you gain features not available in 1.2xx, namely wireless support above and beyond Atheros/Prism 802.11b cards. The details about why this is are outlined on the m0n0wall site - but in a nutshell, it's because of 1.2xx being based on FreeBSD3/4 whereas 1.3 is based on FreeBSD6.x - thus, you gain all the hardware support that the base system brings to the table.

[http://m0n0.ch/wall](http://m0n0.ch/wall)

And the best part is it doesn't require very much in the way of hardware at all, storage space being the easiest to satisfy; 10MB! It's got a web-based administration panel that covers all of it's functionality as well.

Case in point: I have a little old microATX motherboard with a fanless celeron 400 in it, a 128MB stick of PC133 and a 32MB CompactFlash card sitting in a CF -> IDE adapter card that plugs directly into the IDE port. 3 PCI NICs handle connectivity (1 WAN, 1 LAN, and 1 for my WiFi AP). A tiny PicoPSU power supply feeds it 15/22 watts of juice at idle/max-load, which is perfect for a machine you expect to be on 24/7/365 - it costs nearly nothing to run. How much is a desktop going to cost at 250+ watts? ;)

So... of course the decision is up to you, but my recommendation would be to go ahead and continue to use your desktop machine to fiddle with Linux in general, enjoy tweaking & having fun with the UI and learning about it all, etc... but leave the gateway/router/firewall/traffic-shaping bit for a more well-suited software package.

Best of luck in whichever path you choose though! :)

---

### Post by woobla on 2008-05-04
Thanks for the reply xyphur

I will check it out mate, It sounds exactly like I want.

:)

---

### Post by McLogic on 2008-05-07
Ok, I'm at the same place, but would like to still use Ubuntu and not a specialized distribution. The reasons are reliability, price, performance, and power consumption. 

Considering:
[LIST]
[*]I'm going to run the Ubuntu machine, so any additional machine is a waste of power.
[*]That other machine must be bought with my money.
[*]More computers (HD's, PS's, Cables, Ports, etc.) means more points of failure.
[*]The LAN that would connect a two-machine solution is not as fast as the internal data paths in a one-machine solution.
[/LIST]

Choices:
[LIST=1]
[*]If someone knows how to set up **m0n0wall-like tools natively on Ubuntu**, please post here.
.

[*]I guess another option is a **virtual machine with m0n0wall**, like the following. If anyone here has used this with 8.04 (as I know it is a bit more trouble then 7.10) please post here. Even 7.10 experience would be useful.

[http://www.vmware.com/appliances/directory/150](http://www.vmware.com/appliances/directory/150)
[/LIST]

---

### Post by xyphur on 2008-05-07
McLogic: As far as the performance aspect is concerned, you are correct about the internal transfer speeds being leaps and bounds faster. The thing is, and I'm only pointing this out, there is a very VERY slim chance that you (and about 80% of the general population) are using a connection to the internet that is faster than 100Mbit. The bottleneck in any internet gateway setup, no matter how large or small, is the internet connection itself. A typical residential connection is well within the speed constraints of an average 100BaseT ethernet network, and even within the range of most consumer wireless products these days.

Therefore the only other realistic boundaries would be price and power consumption. As for price, assuming you don't already have a spare Pentium board & CPU laying around, you could easily acquire the parts by dumpster-diving, asking people if they have an old uesless machine sitting in their basement or garage, or checking out Craigslist for your area... most times you'll find listings for old computer parts - sometimes even entire machines - in the FREE listings (as in, the stuff being listed costs nothing, just go pick it up)

As you mention power consumption, and old machine with no hard drive, no optical drive, no floppy, and a early model pentium or celeron, or even 486 CPU will draw next to nothing. As I outlined in my previous post, my current m0n0wall machine configuration is WAY overkill for it's role, and yet it's still only drawing less than 25w at full tilt (during boot, for example, which lasts less than 30 seconds as it is booting from CompactFlash). Power consumption this low is akin to having a clock radio plugged in 24/7/365. Even some compact-fluorescent bulbs draw more power than this! :D

The best part of having a seperate gateway running purpose-built software is that if my main desktop machine suffers some unforseen error or malfunction, I still have a working internet connection that I can use in case I need to do research or get files/drivers to fix the problem.

Additionally, I can power off my desktop when I'm not using it, or if I happen to feel like computing elsewhere in the house or outside on the deck with my laptop... again, I still have a functioning - and protected - internet connection, and my desktop isn't eating up a couple hundred watts of juice idling just for this luxury.

I suppose by now it is plainly obvious I am a large fan of m0n0wall. What can I say other than it's a fantastic piece of software, and it works well on hardware that is basically useless for anything else. Food for thought at the very least. :)

EDIT: As for reliability, which I forgot to touch on, the machine I described being my m0n0wall has no moving parts. Fanless CPU heatsink. No hard drive, boots and stores it's config on solid-state CompactFlash media (which also happens to draw FAR less power than a hard drive), power supply is currently a PicoPSU-120 with a switching AC->DC power brick. It used to be powered with an old FlexATX 180w power supply. Even then the only moving part was the 80mm fan in the PSU, which was being run at 5v to keep noise levels down and extend fan life. Power consumption when using the FlexATX was around 30w max load, 20-25w at or around idle. I test power consumption using a Kill-a-Watt power meter ( [http://www.thinkgeek.com/brain/whereisit.cgi?t=kill-a-watt&x=0&y=0](http://www.thinkgeek.com/brain/whereisit.cgi?t=kill-a-watt&x=0&y=0) )

---

### Post by McLogic on 2008-05-09
> **xyphur said:**
> I suppose by now it is plainly obvious I am a large fan of m0n0wall. What can I say other than it's a fantastic piece of software, and it works well on hardware that is basically useless for anything else. Food for thought at the very least. :)

Yes, this is obvious. Some of that info like the 25 watts/hr (roughly 3 USD/month of electricity) is interesting, but not what I (or the OP) was looking for. 

You spend the your whole post telling my why I'm wrong for wanting to run any gateway but your favorite. And if I don't want to run it just the way you do, then I'm wrong for that also.

> **xyphur said:**
> McLogic: The thing is, and I'm only pointing this out, there is a very VERY slim chance that you (and about 80% of the general population) are using a connection to the internet that is faster than 100Mbit. 

I'm more worried about latency. I bet the internal VM networking is much faster then a set of physical devices. This may be especially true with the outdated system that you are running m0n0wall on.

What I want: OS-NIC-Internet
What you have: OS-NIC-Switch-NIC-IRQ-OS-NIC-Internet 

> **xyphur said:**
> McLogic: As far as the performance aspect is concerned, you are correct about the internal transfer speeds being leaps and bounds faster.

I play games and want to do multi-artist collaborative audio on the internet (I play clarinet). Latency is really important in audio. I plug in (get off wifi) to cut a few ms off. I use DSL and pay more money for less speed, as the latency is better then cable. 

[CENTER]Every millisecond counts.[/CENTER] 

[SIZE="3"]xyphur,[/SIZE] If you want to spend a couple of min testing, _and really help me out_, I would appreciate 2 numbers:
Your m0n0wall setup as-is.
Your computer directly connected to the Internet modem.

Using ping & speed tests like:
[http://www.dslreports.com/beta/doctorping](http://www.dslreports.com/beta/doctorping)
[http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)

The ping test is much more important, if you only have time for one.

[CENTER]**Thanks in advance!**[/CENTER]

**To all:** If anyone has any info about running complex gateway tools on Ubuntu, or running M0n0wall as a gateway in a VM please post here.

[LIST=1]
[*]If someone knows how to set up **m0n0wall-like tools natively on Ubuntu**, please post here.
.

[*]If someone has run a **virtual machine with m0n0wall** (like the following link) please post your details here and let us know if it works well.

[http://www.vmware.com/appliances/directory/150](http://www.vmware.com/appliances/directory/150)
[/LIST]

---

