---
title: "Sharing an Outside Wireless connection to the entire house"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by RabidWeezle on 2007-10-22
Here's my goal, I have a wireless connection via a wireless wan in my area to the net and I want to send that wireless connection to my router via dnsmasq to the rest of my network. I need a simple guide to do something like this. I have been lookin all over the wiki with no luck. Something idiot proof basically for hooking up my wired ethernet to the wan input to the router so it can do the rest of the work to providing internet to the rest of the network. Basically my plan is like so:

[hotspot] -> [wireless on laptop] ->[dns/dhcp server (dnsmasq)] -> [router] -> [Rest of Networked Computers]

Anyone with the knowhow of how this could work or how I can just get 1 computer to share the net connection at least would be great

---

### Post by RabidWeezle on 2007-10-23
anyone play around with firestarter? Tried that and I got close... Got the router to get an ip... if anyone has gotten internet connection sharing working at all, lets get it goin :)

---

### Post by RabidWeezle on 2007-11-23
Got it working using internet sharing and such. Did find out something though, xbox 360 *doesn't* need a crossover cable or router to share internet with, just use a standard internet cable and it kinda just figures out what's going on. Now, on normal computers, you do need a crossover cable or (like I did) use a router or hub or switch. Basically I set the ip's static to 192.168.1.10 etc on the client machines with the gateway of the ip of the laptop, the laptop is setup with internet connection sharing as posted on these boards with dnsmasq and ipmasq and it's working like a charm. For the router I had some strange idea I was supposed to  hook the laptop up to the wan port, but this was wrong, it goes on like any other pc to one of the lan ports.

---

