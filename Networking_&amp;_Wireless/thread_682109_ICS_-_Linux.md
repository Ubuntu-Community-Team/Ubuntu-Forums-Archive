---
title: "ICS - Linux"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by drakan290 on 2008-01-29
There's a feature in Windows XP called ICS (Internet Connection Sharing), that allows me to share my wireless card in my laptop over the LAN. It's a roundabout way of sharing the network but i'll tell you exactly how it goes.

Main FiOS connection comes through fibre optics to the wall, routed by Cat5e to the first router (D-Link Xtreme-N [DIR-655]). There are two PC's attached via the integrated Gigabit switch, a game/vent server, and my mom's client (Dell XP Machine) The printer is installed on this machine, and shared using Print Sharing in XP. Attached via Wireless are two MacBooks, one G4 and one Core2Duo, they shouldn't interfere with this though, anyway. Now, I have a Toshiba Satellite A-10 with a PCMCIA D-Link X-Treme N card in it (DWA-652) running Windows XP Professional, using ICS to share the wireless connection over Fast Ethernet (100BaseT). It connects to another router (SMC Barricade [WBR14T-G] 108mbps Wireless-G) which allows wireless to my basement, and provides another DHCP server for the network. Connected to this SMC router are two servers, one Web server, one FTP server, and me, my client PC running Windows XP Pro/Ubuntu 7.10. 
The laptop basically is slow as crap running XP. It's got 256mb of RAM, and it runs extremely slow even in the lowest graphics settings. By slow, I mean it can't even play a movie without stuttering. (Movie goes slow, then skips, sound plays right on through)
So, Firstly, will Ubuntu make my Lappy run a 'lil faster, or not? Secondly, I don't care if it is command line, I just want it to play some movies and route the internet. 

So, is it possible to replace my lappy/router here with an Ubuntu based system? 
If it takes a few hours in Command line, so be it, but I want it to be able to run fast, and NOT drop packets on me.
EDIT: Or even something like NetBSD to run this sharing?
From what I've read, this is called IP Masquerading in Linux/BSD world, so if that can help you guys distinguish what i'm trying to say, so be it, but please help me figure out this problem.
Thanks for reading,
-Brett

---

### Post by cpk1 on 2008-01-29
Simple internet sharing should be very easy. if the device going to the outside world is eth0 then you would do "sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE"  you would also need to do (from a root login, not just sudo) "echo 1 > /proc/sys/net/ipv4/ip_forward". this will let any clients connected to this machine to get to the outside world. from here you would need to give the card going to the network, lets call it eth1 a static ip, which you can do in /etc/network/interfaces. and then you can configure the clients with static ips so that they are in the same network. for instance if eth1 is 192.168.7.1 then the clients would need to be 192.168.7.XXX.  OR you could set up a dhcp server which is also fairly simple to use and then the linux box will serve all the clients their ips.  Hope this answered everything!

---

### Post by drakan290 on 2008-01-29
So, would it be better to go with Ubuntu, or something else like NetBSD?
It doesn't seem hard to do, but I don't want a strain on resources.

---

### Post by cpk1 on 2008-01-30
ubuntu would be fine, and there are already packages for everything you would need. right now I am using kubuntu on a PIII as a router that serves about 15-20 computers and there are no problems that I can see so far (just set it up). would this ubuntu box be doing anything besides be a router? i still dont see it being a strain on resources if it is just sharing with one or 2 other computers...

---

