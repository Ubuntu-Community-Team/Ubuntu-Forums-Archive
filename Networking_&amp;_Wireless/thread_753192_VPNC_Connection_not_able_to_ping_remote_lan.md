---
title: "VPNC Connection not able to ping remote lan"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by quikgyd on 2008-04-12
Greetings All: I am looking to moving to  Ubuntu on an EEEPC or similar. This would be for both play and work. I have a company issued laptop(Win XP) that weighs 6.5 lbs with power supply, which i would love to ditch in place of the two pound EEEPC. However, before I can do that I need to be able to VPN into both  a Contivity(Nortel ) device and a Cisco Network and the trifecta would be to be able to hit Sonic Wall VPN's as well.However the latter is probably a pipe dream : ) . I've started with Cisco , and plan to knock my needs off one at a time.
Currently I am running Ubuntu 7.10 as a vmware machine which is running on my XPbox for testing. I am using vpnc and Kvpnc. My problem is that although I am connected to the vpn and obtain an ip from the Cisco switch,
I can not ping any thing but myself.At the same time I use my company issued laptop with the Cisco VPNclient for Windows and not only am I i able to ping the remote side, I am also able to ping the ipaddress given to my Ubuntu rig running on VMWare. So I am pretty sure that Ubuntu is vpn'd in.In fact both of these machines are at my house and go through my router. So its not my router causing issues. I think I should do a route print in windows and the equivalent in Ubuntu, to see what i may need to add in the way of routes to Ubuntu. Has anybody seen this before. I have no "Firestarter" or equivalent running. Thanks for your time.

---

### Post by bradwilliamson on 2008-04-14
Assuming that the VPN is alive and is actually working, and sometimes that's a very big IF, you should try and connect to something at the far end of the VPN.

It's entirely possible that ping is disabled at the far end firewall. Stupid, but possible.

Try a web browser connecting to an internal web server by IP address and see where you get.

Traceroute can work where ping does not because it uses TCP by default, not ICMP, and the sophomore firewall admins don't catch that.

Also, many VPN clients use sudo to elevate the TUN/TAP interfaces to connect, and you as joe user can't use all features of that connection, so maybe a sudo ping a.b.c.d may work.

VPN's are tricky business in the first place, and the Linux clients are less polished than they could be.

Good luck!
Brad

---

