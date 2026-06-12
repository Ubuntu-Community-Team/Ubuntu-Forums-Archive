---
title: "Problem with networking"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by Jayfaas on 2008-01-12
I have two computers in my room.  One running windows XP and one I just installed Ubuntu on.  They are running off of a Netgear FVS318 router.  the internet port from that router is connected to a port downstairs on a netgear wgr614 wireless(& wired) v7 router, thats connected to a motorola sb5120 modem.  There are two computers connected to the wgr614 router, one xp pro and one vista basic.  I cannot seem to connect to those two computers from my computer, even though the workgroup IS the same on all the computers.  Before I connected to this FVS318 router in my room, I could network to the other XP computer just fine, but now that im behind this router in my room, I cant connect OR see any of the computers.  I dont have any firewalls turned on.  And I need help networking this xp computer in my room to the ubuntu computer right next to it.  Im new to ubuntu, just installed it yesterday.  If someone can help me with getting the xp and vista computers networked, and maybe a lamens terms walkthrough or link to somewhere I can understand how to network the ubuntu computer.  I went to a site to tell me how to setup smbfs, but I couldnt figure it out.  it was goin on about all this stuff I didnt understand :(

---

### Post by ebutton on 2008-01-12
I can help a little.  The first thing is to get rid of the router in your room, replacing it with an Ethernet switch (best) or an Ethernet hub.  A Netgear 4-port 10/100 switch is not expensive.  I'm not familiar with the FVS318, but it may be possible to disable all of its other features (firewall, NAT, DHCP server) and use it as the switch.  I'm not sure.

As a general rule for small business or home networks, add a switch/s to extend the length (maximum cable distance to the furtherest end node) of your network and/or to add additional connection ports.  Adding a router adds unnecessary complexity and usually costs more than a switch.  No single Ethernet cable should be longer than 100 Meters/300 feet and cable patch panels or other physical connections in the path reduce that maximum length.

I use a WGR614 too.  By letting it be the only firewall, NAT service, and DHCP server, all of your DHCP clients are certain to be on the same network.  I've expanded beyond the four WGR614 ports by adding an inexpensive Linksys "EtherFast 10/100 5-Port Workgroup Switch", which works perfectly.

BTW, I've updated my WGR614 firmware a couple of times, so check to see if yours is running the latest version.  I DO NOT think that a firmware upgrade will solve your problem, but it might fix some vulnerability and/or improve overall performance.

Regards,
EdB

---

### Post by Jayfaas on 2008-01-12
only reason I added the fvs318 is because I had it extra.  I bought the wireless router and hooked it up so I could have wifi for my ipod touch.  I ran the router in here, changed it to non-dhcp, and changed the ip to 192.168.1.2 and it works.  Now onto the ubuntu networking problem.  I wanna be able to do that and havent figured it out yet

---

### Post by jonandrews on 2008-01-13
Have a look at my step-by-step Windows / Ubuntu networking guide:

[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

This should help you with taking the mystery out of using SAMBA to achive basic networking.

---

