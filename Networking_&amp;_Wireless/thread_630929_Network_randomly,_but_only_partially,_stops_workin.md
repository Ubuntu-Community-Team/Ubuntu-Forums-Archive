---
title: "Network randomly, but only partially, stops working after a while"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by BrendanM on 2007-12-03
This is one of the stranger issues I've ever encountered. I have a computer running Gutsy where networking seems to randomly stop working after it's been up for anywhere from a few hours to several days. I can't get to websites, or use Synaptic, or ping websites, and I can't connect to samba shares on the box from other computers. What's stranger is that AIM/IRC and DC++ (running on the machine in question) remain connected. It's like connections that were active before whatever-it-is-that-goes-wrong happened stay up, but it can't make or accept any new connections.

"sudo /etc/init.d/networking/ restart" has no effect, but rebooting does fix it for a while until it goes down again.

Needless to say, this is pretty annoying. Does anyone here have any suggestions? I'm not even sure how to start diagnosing the problem. The machine is pretty standard older hardware, and it's a wired connection. I can post details if people think that will help.

---

### Post by miltonr on 2007-12-03
How about switching hub ports to see if the port now being used is flaking out?

---

### Post by jflaker on 2007-12-03
I agree with miltonr.......this is quite possibly a network hub, card or MOST LIKELY a cable issue issue rather than an OS issue.

As you didn't say whether you were wireless or not, I will assume you are wired.  Start with the cheapest part first, the cable.  Cables usually are the primary cause.  Then the network card, then the router.  

I have a suspicion (assuming you are wired) that the cable is going bad.  Otherwise, you will need to start at the wireless card.

---

### Post by BrendanM on 2007-12-03
Thanks for the help guys. I did mention that I was wired (but I sort of slipped it in at the end). I doubt it's the router because there's several other machines on the same router (it's actually in access-point mode) but I will try troubleshooting the hardware.

If that doesn't work, are there any log files I could look at to see if Ubuntu records when the connection drops?

---

### Post by jflaker on 2007-12-03
in SYSTEM>>ADMINISTRATION>>SYSTEM LOG.......look at the daemon.log for IP address assignments and drops........As I have a wireless connection, I am not sure what error you would be looking for

---

### Post by cemptor on 2007-12-04
I have the same issue with a PCI WiFi connection, and it's been happening only in the last one week or so. I've been running nicely on the same hardware for a year, first with Feisty and now Gutsy(upgrade). I think it happened after some upgrades.

The connection functions fine when I reboot, for a while, and then suddenly no DNS and no connectivity. I tried pinging known IP addresses and those do not work either.

When I do a /etc/init.d/networking restart, it starts working for a couple of seconds, until it gets to the DHCP section of the script and then freezes.

Any clues? A lot of people seem to be having the same issue.

---

### Post by randomjohn on 2007-12-04
Add me to the list of those having problems.  I just posted about this too but I guess I didn't have as good a title.  Anyway, I run my ubuntu pc headless and once in a while it just completely drops off the network.  I can't get to it by name or by IP.  I have to physically reboot it, which sucks because it means I can't move it downstairs like I want to.  The only thing it runs is utorrent via wine and webmin.  Other than that, it has a bunch of drives that are mapped on some other pcs running vista and xp and some modded xboxes.

---

### Post by cemptor on 2007-12-17
I have a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) PCI card for my wireless.

I removed the proprietary driver which I was using in Gutsy x86_64 and now my connectivity is much better, It still drops randomly, but only about once or twice a day.

Stil no permanent solution, though. Help would be appreciated.

---

