---
title: "Two computers not mutually pingable (but are from a 3rd machine)"
date: 2017-06-27
forum: Networking &amp; Wireless
---

### Post by rimorob on 2017-06-27
I have the weirdest problem.  I have two computers, A and B, connected to the router by wire, and a laptop, C, connected to the router wirelessly.  I can ping and SSH into A and B from C.  However, I cannot ping A from B and B from A.  Both A and B can reach the router.  Note that I have turned off the firewall on B and that it's not even installed on A.  Also note that I'm connecting to all machines by IP.  Any suggestions?  

P.S. There's a related post here but the solution was to restart the machine that couldn't reach the router, which I tried to no effect (I restarted both A and B).
P.P.S. I'm running Mac OS X on C, an ancient busybox on A, and Ubuntu 16.04 on B.  I have very recently upgraded B from 14.04 and haven't tried connecting to A since, but I think that this upgrade is a red herring (most likely).  I'm kind of leaning towards blaming the router, but I really don't have a clue.

---

### Post by TheFu on 2017-06-27
Please post all the network data for each system.
* IP
* netmask
* routing table

Also, check the simple things - cables, switch ports, can ping the router by IP, can ping 8.8.8.8 and can ping google.com from each system.

On Linux systems, the firewall is built-into the kernel. It is just the end-user interface programs that may or may not be installed.

I cannot help with the non-Ubuntu systems beyond basic network stuff. Sorry.

---

### Post by vocx on 2017-06-29
> **rimorob said:**
> I have the weirdest problem.  I have two computers, A and B, connected to the router by wire, and a laptop, C, connected to the router wirelessly.  I can ping and SSH into A and B from C.  However, I cannot ping A from B and B from A.  Both A and B can reach the router.  Note that I have turned off the firewall on B and that it's not even installed on A.  Also note that I'm connecting to all machines by IP.  Any suggestions?  

P.S. There's a related post here but the solution was to restart the machine that couldn't reach the router, which I tried to no effect (I restarted both A and B).
P.P.S. I'm running Mac OS X on C, an ancient busybox on A, and Ubuntu 16.04 on B.  I have very recently upgraded B from 14.04 and haven't tried connecting to A since, but I think that this upgrade is a red herring (most likely).  I'm kind of leaning towards **blaming the router**, but I really don't have a clue.
I've had this issue before and frankly I have no idea what the problem is. I feel it is black magic essentially.

For years I used a single computer so I never had issues with connecting more than one device to my router. Nowadays it is not uncommon for people to have 10 or more devices in a household including cellphones, smart TVs, laptops, desktops, and tablets, so connectivity problems between the devices seems to be more prevalent.

My particular case was with three machines, running Ubuntu 16.04, and two Raspberry Pi, running Raspbian Jessy. Occasionally I could ping and ssh from B to C, and from C to B, but not from and to A. It was frustrating. I read a bunch of stuff, about DNS, about DNS lists in the router, about SSH, about the avahi/zeroconf/Bonjour service which makes computers recognize each other in a network without a centralized server, about adding static IP addresses to the computers, and my other things.

Eventually, after many reboots, I felt there was really nothing I could do. I just accepted my faith and went on my way. Eventually, the machines could locate each other, by hostname or IP address, everything just worked as intended! I didn't really have to do a thing, as the problem seemed to fix itself.

I feel many network issues are solved with time. I am not entirely familiar with the network protocols but I feel they work on the basis of caching information, caching IP addresses, and resolving those addresses. This seems to take time, like the router, or the computers themselves, they all have to store and synchronize this information, in order for them to be found in a network. You would think this should happen fast, as data is transmitted and processed at CPU speeds (Gigahertz). There is no reason a computer should take more than a millisecond looking up an address in a database of IP addresses, and yet here we are. Network connectivity is a mystery to me.

This is just speculation but another issue I imagine is the compliance to standards. Since Linux is open source it gives me a lot of confidence it is following networking standards set by the IEEE, ITU, ISO, or whoever. But I don't trust hardware manufacturers, router manufacturers, WiFi card manufacturers, Windows operating systems, etc. to follow the standards. Maybe they add a bit of code to optimize a specific functionality which makes software adhering strictly to the standards not work. I feel this is the case with web browsers. Apparently Firefox sticks closely to the W3C standards, while Internet Explorer has had quirks for years making website developers try to handle their special behavior.

---

### Post by TheFu on 2017-06-30
Networking is not black magic. It behaves as expected 99.9999% of the time. No surprises.

There are occasional incompatibilities between different router and switch vendors and there is always a chance for bad/corrupt firmware and software, but outside those edge situations, it just works.  I haven't seen drastically incompatible networking since everyone moved to 1000-base-tx networking. With the 10/100 stuff, nortel, baynetworks and cisco didn't always get along.  Sometimes cisco, d-link and netgear have issues, but I haven't seen those much.  

Had a few tablets and smartphones have issues with wifi connections. There was a bug in their software, not with the network equipment here.  The fix was the reboot the android device. Happened about 2 times a year, so while frustrating at the time, it wasn't a big deal.

If you stay with standard, wired Intel network cards, almost all of these issues go away. No fighting with issues, drivers, weirdness.

I run my home network with very strict controls.  Effectively ZERO dynamic IPs are used.  Portable devices all get their same IP thanks to DHCP reservations.  My Nexus phone is always ... 172.22.22.98, for example.  Networked TV tuners always have the same IPs too. If they don't, then the DHCP server for the LAN is down (which happened yesterday).

Anyway - no black magic. Just a common, simple, IPv4 network understanding is needed.  I can suggest ways to gain that understanding, if you like.

---

### Post by rimorob on 2017-07-29
To clarify, A and B can reach other computers on the network by name and IP.  Both can find each other's IP (meaning, router's DNS works), but neither can connect to the other by IP.

---

### Post by cariboo on 2017-07-29
> **TheFu said:**
> Please post all the network data for each system.
* IP
* netmask
* routing table

Also, check the simple things - cables, switch ports, can ping the router by IP, can ping 8.8.8.8 and can ping google.com from each system.

On Linux systems, the firewall is built-into the kernel. It is just the end-user interface programs that may or may not be installed.

I cannot help with the non-Ubuntu systems beyond basic network stuff. Sorry.

@rimorob  if you aren't sure how to provide the info that TheFu asked for use the following commands on each computer:

```
ifconfig
```

for ip address and netmask and

```
route
```

for the routing table.

---

### Post by rimorob on 2017-07-29
Found a solution, which is to add the following to the router's startup command:
swconfig dev eth0 set enable_vlan 1
swconfig dev eth0 set apply

Apparently it's a known dd-wrt bug.  It may be fixed in more recent releases but my router is reasonably old.

---

