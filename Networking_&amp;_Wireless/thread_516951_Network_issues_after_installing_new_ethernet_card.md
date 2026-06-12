---
title: "Network issues after installing new ethernet card"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by AceRimmer on 2007-08-03
Hello.  I need some help here.  

I had been running my home network through a Coyote Linux router plugged into a switch.  Well the router died. I used to have my machine set at a static IP address and subnet with the router as the gateway and DNS.  I had that machine as 192.168.0.66 and the DNS and gateway set as the router which was at 192.168.0.1 on eth0.  So I pulled a network card out of that router box and put it in my Ubuntu machine.  Ubuntu saw it and appeared to set it up fine.   Now I have eth0 and eth1.  I plugged the DSL cable from the modem into the old network card which was eth0 and changed that to automatic IP and ran pppoeconf to set it up.  Everything went fine, but both network cards were set to automatic.  eth1 runs to my switch, which lights up and shows that port 2 which the cable is plugged into is active.  Ok, so I have DSL connection now but I cannot connect to my home network and the other PC which has a static IP as well.  I go to network setup and change eth1 to  a static IP, give it 192.168.0.66 and subnet of 255.255.255.0 and no gateway.  Ubuntu says its switching interface and then I lose internet.  I then notice that the DNS entries that pppoeconf setup in DNS are set back to the old router ip of 192.168.0.1 and I cannot get internet even if I manually put the ISP DNS values back in.  So I run pppoeconf again and redo it.  I get internet back but I still cannot see the network which is setup as workgroup MSHOME on the WinXP box plugged in. I switch the eth1 to DHCP as well and now I lose DSL.  I can't ping the other machine either. 

What is going on?  I want to ultimately share my DSL through this box into the XP machine until I get a new router, but that may be a couple months. Why would I not be able to see the network? I plugged the cables in, the switch shows both ports from both machines lit up so they should be connected right?  The switch was working fine until I did the change from the router so I don't think that is messed up. 

Thanks for any help.  I don't know the networking stuff on this side as well as Xp and I'm confused.  

My first network card is a motherboard based card I assume that it would stay eth0 when I put int the new PCI card right?

---

### Post by AceRimmer on 2007-08-04
Well I tried switching to a different hub and still no dice.  I don't understand this.

---

