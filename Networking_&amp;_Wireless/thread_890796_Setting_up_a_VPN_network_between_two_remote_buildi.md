---
title: "Setting up a VPN network between two remote buildings"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by KolosoK on 2008-08-15
Hello,

I would like to set up a VPN connection between two buildings, one of which has an Ubuntu server that I recently set up. The buildings are just two miles apart. The building that contains the server has a dedicated T1 connection with a static IP and the other building has a dedicated 1/2 T1 connection with a static IP.

Here is my task: Connect everyone in the building that does not have the server to the building that does have the server so that clients are able to access this server and do network directory browsing (I have Samba set up for Windows file sharing). All clients are using Windows machines.

Basically, I would like client machines from both buildings to be able to access the server through a local IP address (192.168.x.x or 10.x.x.x).

So far I tried the following:

- Setting up a PPTPd server. This worked, but unfortunately the router at the remote building is unable to connect more than one client to the server. I keep getting error 619, and some quick research showed that this is because the router throwing out the outgoing connection is unable to sort the packets correctly.
- Using a Linksys VPN wireless router at the building with the server. Setting up accounts requires changing the IP range to 10.x.x.x, which I am unable to do at this time because that is the IP range of another router at the building which handles customer connections (they are on their own "branch" network that has no access to anything but internet browsing).

What would be the best course of action for me?

- I was thinking of trying OpenVPN instead of PPTPd  and setting it up using IPsec (it can handle multiple connections from the same source, right?)
- A VPN tunnel between routers at the two buildings? How much would this cost and what is the best hardware for the price available for this task?

Thank you for your help!

---

### Post by SpaceTeddy on 2008-08-15
sound like you want to do what i describe in this [[COLOR="Blue"]tutorial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127"). I use OpenVPN to accomplish the task and have done this. 
For performance reasons i would suggest you try part one first - that would mean you have two different subnets. Part II is only needed i you need to merge the networks together as one network.

If you get stuck on the tutorial - just ask. I'll try to explain and help you as best i can.

hope we can get this to work :)

---

### Post by KolosoK on 2008-08-15
Thanks, I'll check it out.

EDIT: Wow, that looks awfully complicated. :( Do I have to have two servers, one on each network?

EDIT 2: Also, would it be easier to set up the bridge using two CISCO Linksys routers, one at each location?

EDIT 3: Would it be even easier to have individual users connect to a VPN server on the ubuntu machine, the way I was doing it in the first place? If so, what package should I use. PPTPd only allows for one connection from each individual gateway, which sucks.

---

### Post by SpaceTeddy on 2008-08-15
it's not all that complicated - i just explained a lot to try to make this as clear as possible :) but you do need two computers (one on each end) that hold the bridge.
As for clients - yes. Openvpn can do that too. I've also written a tut for that [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5076501&postcount=4"). That is the setup for a dialin openvpn server. 

as i said, i can explain pretty much anything about that setup - you just need to ask. Also, this would not take me more than an hour to do. So it's not that hard... or i just know what i am doing :)

hope it helps...

---

### Post by KolosoK on 2008-08-15
Hmm, I actually did find your guide and attempted to use it before posting this thread :)

The problem is that I will not be able to set up private client keys on everyone's computer. There's just too many users. Plus, I will not be working at the place in three weeks, so they would like me to set it up so users can connect simply using a name and password and still have it be semi-secure.

Today they bought two Cisco Linksys Business routers with VPN and tunneling compatibility. Next week I will play around with them and see if I can use them to create the bridge.

Using computers as routers and creating a bridge is not an option for me right now, so I will try that next, and if it fails, I will definitely ask you more about OpenVPN.

Thanks for the help :)

---

