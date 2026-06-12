---
title: "Massive networking issues"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by Humbie on 2008-11-10
As quite a novice user @ linux, I'm having, as the topic suggests, a random load of issues that pop up when they feel like it...

So what I did was install Ubuntu 8.10 amd64(desktop edition) on my laptop.
Here at my home, we have a quite complicated networking setup which goes as follows:

inet - switch - wlan-router (1st floor) - lan-router (2nd floor - my room)

So what I want to do is... be able to connect wirelessly to my wlan-router @ 1st floor AND be able to connect wired to my lan-router @ 2nd floor - my room.

Problem 1:
When I connect wired to the lan router:
First time => The connection succeeds but I don't have inet-access (maybe because lan-router sets own ip as primary dns through dhcp but this has no issues whatsoever with winxp or vista).
Second time => If I disconnect and reconnect, the connection tries getting a new IP from the dhcp, but eventually doesn't get one and stays diconnected.

Problem 2:
I've only got my wireless connection to work ONCE! (and I don't remember how... :()
My interface is wlan0 and is an Intel Wireless 4965AGN
The thing is, my wlan-router is set-up so that it DOESN'T distribute IP's over the wireless network (and I've tried switching it on again but that doesn't help my connection either)

My wlan is wpa2-personal secured and has wireless-N (so 300MB/s if it would work and quite a good range).

What I have tried is:
1. Working with wpa_passphrase & wpa_supplicant which eventually did nothing for me.
2. Working with NetworkManager, which worked once but after reboot the connection was lost again (go figure!).

What DOES work:
1. Wired connection - connected to inet directly
2. Wired connection - connected to wlan-router directly

I seriously hope ANYONE here is capable enough to help me (and I seriously hope that they can come up with something I can do command-line because I would like to try and set up a server on that laptop once I know it can connect).

Hoping for an answer ASAP (thanks in advance),


Humbie

---

