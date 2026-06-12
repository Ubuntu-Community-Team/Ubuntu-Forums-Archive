---
title: "Auto DHCP fail and staticly set IP can't hit router, need assistance"
date: 2014-05-26
forum: Networking &amp; Wireless
---

### Post by mtweldon on 2014-05-26
Ubuntu 13.1
Router: Asus RT N66U

trying to remember this all from my head as I'm currently at work right now.

Went on vacation for 3 days and come back to my computer not being able to communicate with my router for some reason.

I leave my computer set to a static IP (192.168.1.8) router is (192.168.1.1) 

upon coming home, I can no longer ping 192.168.1.1 or do anything network related. When I attempt to do DHCP it just cycles until it fails. 

looking at the connected clients list from another computer shows that the MAC for my ubuntu box never even hits the client list on the router.


I tried to do an IP route and I get ~~ this:

vmnet1 - 172.x.1
vmnet8 - 172.x.2
eth0 192.168.1.1 

(I do have vmworkstation running for pfsense - but it can't pull an IP either) 

or something similar... is it trying to hit the 172.x IPs to route and it fails? I don't know a whole lot about networking.

weirdly enough, if I plug in the cable modem directly and then use DHCP, I'm able to establish an IP just fine.

ran out of time, but, I'll attempt with my windows computer to plug in via cable and see if I can pull an IP as well, worked fine on wireless. 

I've completely restored the router to default and reboot the ubuntu box multiple times, no dice, I don't know why this randomly happened.

I also have another older router RT  N56U I'll attempt when I get off work.

I just got the 66U about 2 weeks ago, but everything has been working fine up until a couple days ago it looks like.

Looking for any advice / suggestions

---

### Post by Rsxhawk on 2014-05-27
So you went on vacation and when you came back it now can't connect.  Sounds like you might have experienced a power outage at your house over the weekend possibly and when everything came back up, some other device on our network grabbed 192.168.1.8 before your PC could come online and now there is an IP conflict, i.e. two devices using the same IP.  I would check your router and see what MAC addresses it sees mapped to 192.168.1.8 and see if they match your PC or some other device on your network.  The MAC address is the hardware address of your NIC on your PC, its unique to the device its on.  If your router has the capability to see connected wired clients with something like a MAC table, thats where I would look.  Or something to try even faster, just change the static IP of your PC to something at the top of the /24 you're using.

192.168.1.0/24 - Basically means you have between .2 and .254 for usable addresses, since .1 is being used by the router.  Make your PC something high like 192.168.1.250 and see if it helps.  

Or your router could just be borked.

---

