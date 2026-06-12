---
title: "Wireless Bridge"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by sci-fi guy on 2008-07-27
I am wanting to try Debian as my main OS for a while. I have installed it before on other machines, but all of them had a wired connection to my router, while my main machine uses a WiFi connection. I want Debian to be connected to the Internet for updates during the install, so I figure I have three options:
[LIST]Get WiFi to work during the Debian install.[/LIST]
[LIST]Move my machine to the router for a wired link.[/LIST]
[LIST]Use a recently acquired Belkin router to create a wireless bridge and have a wired connection to that.[/LIST]
I would prefer to do option 3 because it is beyond my current level of expertise, I have a collection of computers near my main one that would benefit from this (no wifi cards), and it is a skill likely to be the most useful in the future.

Here's my current setup:
Network 1
[LIST]Netgear WGT624v3 WiFi router connected to the modem (WPA2 encryption)[/LIST]
[LIST]Parent's machine connected to the Netgear router by WiFi (SNAFU)[/LIST]
[LIST]My brother's laptop, also connected by WiFi (Charlie [he's the one that named it])[/LIST]
[LIST]My machine, again connected by WiFi. (Tux)[/LIST]

Network 2
[LIST]Belkin F5D7230-4v9 WiFi Router (not connected to the net, WiFi off right now, being used strictly as a wired router)[/LIST]
[LIST]My machine again[/LIST]
[LIST]Vintage iMac (iMac)[/LIST]
[LIST]Compaq iPaq Internet appliance thingy (no OS on it yet, no not named)[/LIST]

So anyways, I want to use the Belkin Router as a wireless bridge to give Network 2 Internet connectivity, but I wasn't able to get it working after fiddling with it all day yesterday. Help, please?

---

### Post by kevdog on 2008-07-27
So basically the two routers will connect wirelessly?  The only way I know how to do this (which I have done with two setups), is for router #2 (the wireless bridge) is to run either dd-wrt or openwrt.  I personally use dd-wrt.  Possibly one of the two routers can be flashed with the dd-wrt firmware -- you would have to check on the website of dd-wrt to confirm compatibility.  I'm thinking however that both your routers most likely have Atheros chipsets, and dd-wrt/openwrt is for broadcom chipsets, so this solution may not be applicable for you.

---

### Post by sci-fi guy on 2008-07-27
> **kevdog said:**
> *snip*

Neither router's version is listed as compatible with either dd-wrt or openwrt. The model numbers are, but not the versions. But the Belkin router theoretically does have the ability to bridge (see screenshot)

---

### Post by kevdog on 2008-07-27
Shouldnt the belkin router be #1 and the netgear #2 then?

---

### Post by sci-fi guy on 2008-07-28
Looking at it again, I think you may be right. Thank you for catching that. I'll try it and get back to you.

---

