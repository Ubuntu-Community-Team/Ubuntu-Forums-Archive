---
title: "VPN questions; OpenVPN, Hamachi, Baldur's Gate..."
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Mr. Picklesworth on 2008-06-04
Alright, sorry about the vague thread title. Some friends and I are trying to set up a Baldur's Gate multiplayer game, but there is a lot of trouble to be had in setting up a session over the Internet. (Local network works fine). After some fiddling, it seems that a VPN would do the trick.

The thing is, I know very little about VPNs.

Are VPN setups universal? For example, could I connect to a Hamachi server using the OpenVPN client that is so nicely built in to NetworkManager?

Alternatively, is there a nice Windows GUI for OpenVPN that I could force my friends to use? (Or a nice Linux GUI for Hamachi? Their CLI tool is weird).

---

### Post by SpaceTeddy on 2008-06-06
> **Mr. Picklesworth said:**
> Alright, sorry about the vague thread title. Some friends and I are trying to set up a Baldur's Gate multiplayer game, but there is a lot of trouble to be had in setting up a session over the Internet. (Local network works fine). After some fiddling, it seems that a VPN would do the trick.

possibly, yes... maybe... i have never played that before :) so don't expect any help with the game itself.

> **Mr. Picklesworth said:**
> 
The thing is, I know very little about VPNs.

THAT is not a problem. There is always something that one does not know. As long as you are willing to learn... no problem at all !
> **Mr. Picklesworth said:**
> 
Are VPN setups universal? For example, could I connect to a Hamachi server using the OpenVPN client that is so nicely built in to NetworkManager?

No, VPN-Clients need the same sever as the software. For example, a business VPN usually runs the IPSEC protocol while OpenVPN runs purely on SSL/TLS. they are two fundamentally different protocols. 

> **Mr. Picklesworth said:**
> 
Alternatively, is there a nice Windows GUI for OpenVPN that I could force my friends to use?

[http://openvpn.se]("http://openvpn.se")> **Mr. Picklesworth said:**
>  (Or a nice Linux GUI for Hamachi? Their CLI tool is weird).
No idea about that - never used hamachi in linux.

Ok, that answered, here is the deal what i ***think*** you need. This can be, of course, entirely wrong. 

I ***think*** what you need is broadcast support. That means, a computer is sending out pakets on the local lan (called broadcasts) which other computers pick without them being directly addressed to them. The problem is, OpenVPN does not support that by default - it needs to be configured. For that, you will need a bridged vpn and a dchp-server for the vpn. The setup is a bit... tricky, but it should work. Unfortunately, this will require some heavy understanding on your part. 

So, if you want to do that, i can run you through a few basic steps of how to get that up and running. I'd suggest that you try to find a gui for hamachi first, tho - since that is way easier and has the broadcast support build in by default. 

Btw, broadcast support means that layer 2 is forwarded - so we are speaking of the MAC layer instead of IP layer here... that is just for for totally confusing you :)

I know this post probably does not help you in accomplishing anything. If you need more precise instructions for openvpn - just ask.

hope it (somewhat) helps :)

---

### Post by colo on 2008-06-06
If you intend to play BG under Wine in multiplayer, chances are you'll be disappointed: last time I checked, Wine did not support the DirectPlay (DirectX IP-Networking) API.

I happened to play BG2 via Hamachi under Windows with some of my friends about a year ago, and the performance was horrible as soon as more than two clients were hooked onto the same VPN. I don't know how OpenVPN would perform for gaming, but in our office, it's bliss, and not really hard to set up, either.

I'm not entirely sure BG/DirectPlay communicates/discovers hosts via broadcasts at all; you might as well try a routed OpenVPN setup first, and directly specify the IP-address of the host hosting your gaming session.

Good luck! :)

---

