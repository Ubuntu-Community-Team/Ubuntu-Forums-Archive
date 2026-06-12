---
title: "[SOLVED] Sharing between two Ubuntu desktops"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by conphara on 2008-12-12
I have really run into some nasty problems with my home network. The goal is to connect my desktop (Intrepid) with my laptop (upgraded Intrepid) so I can transfer files from the laptop to the desktop pc. Worked without much trouble with Hardy, but isn't working with Intrepid.
I have given both machines fixed IPs (desktop: 192.168.0.1,laptop:192.168.1.1). One issue is I can't ping either machine from the other using Gnome-nettool. It can ping itself but not the other on the network. But my cable is crossed, has worked before up until now, I can see when I'm shutting down one of the machine on the other machine telling me the connection is lost and connected when both are one, plus it transfered files once doing with the IP-addresses. I've tried Samba (with/without sambafs, winbind), NFS, SSH using standard guides. Nothing across through. I can't see anything other then one machine in Network (Places). I configured Samba using shares-admin and system-config-samba. SSH complained something about port 22 wasn't open. I tried smbtree -a which only shows the one machine, not the other on the "network".
Another thing is the laptop is dualbooted with XP and I can't see the desktop pc under network places or ping the XP machine from the desktop.
I've tried other crossed cables - nothing, still no connection. Something been blocking connections on my desktop pc but I don't know.

Please help. This is so frustrating.

---

### Post by Kellemora on 2008-12-12
Hi Con

Use IP numbers 192.168.1.101 and 192.168.1.102

And if you're not using a Router, Hub or Switch, you will need a crossover cable to connect only two machines together.  
Cheaper to buy a Router in the long run, saves MEGA headaches and protects your system from intruders fairly well.

TTUL
Gary

---

### Post by SIGTERMer on 2008-12-12
> **Kellemora said:**
> 
Use IP numbers 192.168.1.101 and 192.168.1.102


some routers reserve IPs ranging from 192.168.*.100 to 192.168.*.199 for there dynamic address pool. this might cause problems


dude, first of all, the two IPs you chose (192.168.0.1 & 192.168.1.1) are on deferent subnets if you submask is set to 255.255.255.0 which is the default (on both ubuntu and most routers) chose an IPs on the same subnet. for example:
192.168.1.10 PC
192.168.1.11 Laptop

this is assuming that you use a switch/hub

if you use a router, check the ip of the router (which is almost always 192.168.1.1 - you used the same ip for your pc) if so, choose an ip that is not in the routers address pool (check router documentation). 
if you don't know what that is, connect to your network normally (DHCP/not static) and then type the following at the terminal:

iwconfig

this will give you all every IP assigned to each network interface. use that ip to connect to the computer

sorry if i got too carried away,
SIGTERMer

---

### Post by conphara on 2008-12-16
It worked!! Using IP numbers 192.168.1.101 and 192.168.1.102 solved my problem.
From old habit (Windows days) I have always used 192.168.0.1 as the host and 192.168.1.1 as the guest linked with a wired cable. And it worked in Hardy but not on Intrepid. It really doesn't matter what I use, just as long as the IP's doesn't screw up the connection.

Many thanks...

---

